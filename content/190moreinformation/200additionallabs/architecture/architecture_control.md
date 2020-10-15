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

You can enable or disable pod security policy using the az aks update command. The following example enables pod security policy on the cluster name myAKSCluster in the resource group named myResourceGroup. (change cluster name and resourcegroup to one used in your tenant)

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


Please note, the Pod Security Policy incidents can take some time to resolve. Try checking back later after the Shift-Left lab.

