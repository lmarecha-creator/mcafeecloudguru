---
title: "Resolve Incidents and Rescan"
date: 2020-02-24
weight: 30
---

Now let's fix some of these issues! First, log into your Azure tenant. Within here, see if you can successfully:


To resolve the Pod Security Policy issue we reviewed earlier, we need to put on our DevOps hat and head to Azure Cloud Shell. Pull up theAzure Cloud Shell and run the following command.

Install aks-preview CLI extension

```
# Install the aks-preview extension
az extension add --name aks-preview

# Update the extension to make sure you have the latest version installed
az extension update --name aks-preview
```
Register pod security policy feature provider

```
az feature register --name PodSecurityPolicyPreview --namespace Microsoft.ContainerService
```
It takes a few minutes for the status to show Registered. You can check on the registration status using the az feature list command:


```
az feature list -o table --query "[?contains(name, 'Microsoft.ContainerService/PodSecurityPolicyPreview')].{Name:name,State:properties.state}"
```
When ready, refresh the registration of the Microsoft.ContainerService resource provider using the az provider register command:

```
az provider register --namespace Microsoft.ContainerService
```

### Enable pod security policy on an AKS cluster

You can enable or disable pod security policy using the az aks update command. The following example enables pod security policy on the cluster name myAKSCluster in the resource group named myResourceGroup. (change cluster name and resourcegroup to the one used in your tenant)

```
az aks update \
    --resource-group myResourceGroup \
    --name myAKSCluster \
    --enable-pod-security-policy
```
### To view the policies available, use the kubectl get psp command, as shown in the following example

```
$ kubectl get psp

NAME         PRIV    CAPS   SELINUX    RUNASUSER          FSGROUP     SUPGROUP    READONLYROOTFS   VOLUMES
privileged   true    *      RunAsAny   RunAsAny           RunAsAny    RunAsAny    false            *     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim

```
The privileged pod security policy is applied to any authenticated user in the AKS cluster. This assignment is controlled by ClusterRoles and ClusterRoleBindings. Use the kubectl get rolebindings command and search for the default:privileged: binding in the kube-system namespace:

It's important to understand how these default policies interact with user requests to schedule pods before you start to create your own pod security policies. In the next few sections, let's schedule some pods to see these default policies in action.

#### Create a test user in an AKS cluster

By default, when you use the az aks get-credentials command, the admin credentials for the AKS cluster are added to your kubectl config. The admin user bypasses the enforcement of pod security policies. If you use Azure Active Directory integration for your AKS clusters, you could sign in with the credentials of a non-admin user to see the enforcement of policies in action. In this article, let's create a test user account in the AKS cluster that you can use.

Create a sample namespace named psp-aks for test resources using the kubectl create namespace command. Then, create a service account named nonadmin-user using the kubectl create serviceaccount command:

```
kubectl create namespace psp-aks
kubectl create serviceaccount --namespace psp-aks nonadmin-user
```
Next, create a RoleBinding for the nonadmin-user to perform basic actions in the namespace using the kubectl create rolebinding command:

```
kubectl create rolebinding \
    --namespace psp-aks \
    psp-aks-editor \
    --clusterrole=edit \
    --serviceaccount=psp-aks:nonadmin-user
```
#### Create alias commands for admin and non-admin user

To highlight the difference between the regular admin user when using kubectl and the non-admin user created in the previous steps, create two command-line aliases:

The kubectl-admin alias is for the regular admin user, and is scoped to the psp-aks namespace.
The kubectl-nonadminuser alias is for the nonadmin-user created in the previous step, and is scoped to the psp-aks namespace.

Create these two aliases as shown in the following commands:

```
alias kubectl-admin='kubectl --namespace psp-aks'
alias kubectl-nonadminuser='kubectl --as=system:serviceaccount:psp-aks:nonadmin-user --namespace psp-aks'

```
#### Test the creation of a privileged pod

Let's first test what happens when you schedule a pod with the security context of privileged: true. This security context escalates the pod's privileges. In the previous section that showed the default AKS pod security policies, the privilege policy should deny this request.

Create a file named nginx-privileged.yaml. We are going to use Azure Cloud Shell editor:

```
code nginx-privileged.yaml 
```
![cspm2](/images/mvcscan/azure-code.png?classes=border,shadow)

Paste the following YAML manifest
 
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-privileged
spec:
  containers:
    - name: nginx-privileged
      image: nginx:1.14.2
      securityContext:
        privileged: true
```
Press Ctrl+S to save or right click and click on save.

Create the pod using the kubectl apply command and specify the name of your YAML manifest using the Azure Cloud Shell editor:

```
kubectl-nonadminuser apply -f nginx-privileged.yaml
```

The pod fails to be scheduled, as shown in the following example output:

```
$ kubectl-nonadminuser apply -f nginx-privileged.yaml

Error from server (Forbidden): error when creating "nginx-privileged.yaml": pods "nginx-privileged" is forbidden: unable to validate against any pod security policy: []

```
#### Test creation of an unprivileged pod

Create a file named nginx-unprivileged.yaml. We are going to use Azure Cloud Shell editor:

Paste the following YAML manifest

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-unprivileged
spec:
  containers:
    - name: nginx-unprivileged
      image: nginx:1.14.2

```

Create the pod using the kubectl apply command and specify the name of your YAML manifest:

#### Create a custom pod security policy

```
kubectl-nonadminuser apply -f nginx-unprivileged.yaml

```
The pod fails to be scheduled, as shown in the following example output:
```
$ kubectl-nonadminuser apply -f nginx-unprivileged.yaml

Error from server (Forbidden): error when creating "nginx-unprivileged.yaml": pods "nginx-unprivileged" is forbidden: unable to validate against any pod security policy: []

```

Now that you've seen the behavior of the default pod security policies, let's provide a way for the nonadmin-user to successfully schedule pods.

Let's create a policy to reject pods that request privileged access. Other options, such as runAsUser or allowed volumes, aren't explicitly restricted. This type of policy denies a request for privileged access, but otherwise lets the cluster run the requested pods.

Create a file named psp-deny-privileged.yaml and paste the following YAML manifest using the Azure Cloud Shell editor:

```
code psp-deny-privileged.yaml
```

Paste the following YAML manifest

```
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: psp-deny-privileged
spec:
  privileged: false
  seLinux:
    rule: RunAsAny
  supplementalGroups:
    rule: RunAsAny
  runAsUser:
    rule: RunAsAny
  fsGroup:
    rule: RunAsAny
  volumes:
  - '*'
```
Press Ctrl+S to save or right click and click on save.


Create the policy using the kubectl apply command and specify the name of your YAML manifest:

```
kubectl apply -f psp-deny-privileged.yaml
```

To view the policies available, use the kubectl get psp command, as shown in the following example. Compare the psp-deny-privileged policy with the default privilege policy that was enforced in the previous examples to create a pod. Only the use of PRIV escalation is denied by your policy. There are no restrictions on the user or group for the psp-deny-privileged policy.

```
$ kubectl get psp

NAME                  PRIV    CAPS   SELINUX    RUNASUSER          FSGROUP     SUPGROUP    READONLYROOTFS   VOLUMES
privileged            true    *      RunAsAny   RunAsAny           RunAsAny    RunAsAny    false            *
psp-deny-privileged   false          RunAsAny   RunAsAny           RunAsAny    RunAsAny    false            *          
```
#### Allow user account to use the custom pod security policy

In the previous step, you created a pod security policy to reject pods that request privileged access. To allow the policy to be used, you create a Role or a ClusterRole. Then, you associate one of these roles using a RoleBinding or ClusterRoleBinding.

For this example, create a ClusterRole that allows you to use the psp-deny-privileged policy created in the previous step. Create a file named psp-deny-privileged-clusterrole.yaml and paste the following YAML manifest using the Azure Cloud Shell editor:

```
code psp-deny-privileged-clusterrole.yaml
```
Paste the following YAML manifest

```
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: psp-deny-privileged-clusterrole
rules:
- apiGroups:
  - extensions
  resources:
  - podsecuritypolicies
  resourceNames:
  - psp-deny-privileged
  verbs:
  - use
```
Press Ctrl+S to save or right click and click on save.

Create the ClusterRole using the kubectl apply command and specify the name of your YAML manifest:

```
kubectl apply -f psp-deny-privileged-clusterrole.yaml
```

Now create a ClusterRoleBinding to use the ClusterRole created in the previous step. Create a file named psp-deny-privileged-clusterrolebinding.yaml and paste the following YAML manifest:

```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: psp-deny-privileged-clusterrolebinding
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: psp-deny-privileged-clusterrole
subjects:
- apiGroup: rbac.authorization.k8s.io
  kind: Group
  name: system:serviceaccounts
```

Create a ClusterRoleBinding using the kubectl apply command and specify the name of your YAML manifest:

```
kubectl apply -f psp-deny-privileged-clusterrolebinding.yaml
```
#### Test the creation of an unprivileged pod again

With your custom pod security policy applied and a binding for the user account to use the policy, let's try to create an unprivileged pod again. Use the same nginx-privileged.yaml manifest to create the pod using the kubectl apply command:

```
kubectl-nonadminuser apply -f nginx-unprivileged.yaml
```
The pod is successfully scheduled. When you check the status of the pod using the kubectl get pods command, the pod is Running:

```
$ kubectl-nonadminuser get pods

NAME                 READY   STATUS    RESTARTS   AGE
nginx-unprivileged   1/1     Running   0          7m14s
```
This example shows how you can create custom pod security policies to define access to the AKS cluster for different users or groups. The default AKS policies provide tight controls on what pods can run, so create your own custom policies to then correctly define the restrictions you need.


Now that we've updated our PSP policy, let's kick off another CSPM scan

![cspm2](/images/mvcscan/azure-scan.png?classes=border,shadow)


Hover over the INCIDENT tab and choose POLICY INCIDENT SUMMARY. You'll be able to see that a few of the incidents have automatically moved to a Resolved status. This drastically reduces the number of incidents your infosec teams need to review! 

![cspm2](/images/mvcscan/AKS-resolved.png?classes=border,shadow)

Please note, the Pod Security Policy incidents can take some time to resolve. 

Furthermore, Autonomous Remediation also works for DLP Incidents. In a production environment, if the files within the S3 bucket were deleted, the incidents would automatically be moved to a Resolved status.

Delete the NGINX unprivileged pod using the kubectl delete command and specify the name of your YAML manifest:

```
kubectl-nonadminuser delete -f nginx-unprivileged.yaml
```
