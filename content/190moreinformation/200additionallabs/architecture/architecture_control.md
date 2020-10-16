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

Now run:

```
kubectl edit psp
```

This will pull up the following screen, allowing you to edit the file with Vi commands. Here is a quick cheatsheet on Vi commands, but further information is available here:

https://kb.iu.edu/d/afdc

Move the cursor to around where you want to modify. Press the Insert key on your keyboard to modify (drop "into" the document). Once modified, press the Insert or Escape key to stop modifying.

![AR](/images/mvcscan/cspmresolve02.png?classes=border,shadow)

Here is what the modification should look like.

![AR](/images/mvcscan/psp-resolve1.png?classes=border,shadow)

![AR](/images/mvcscan/psp-resolve2.png?classes=border,shadow)

Make sure you no longer see --- INSERT --- at the bottom of the screen, which lets you know you are no longer modifying.

Then press the following keys in order to issue a command to write and quit:

1. :
2. w
3. q

Please note, the Pod Security Policy incidents can take some time to resolve. Try checking back later after the Shift-Left lab.

