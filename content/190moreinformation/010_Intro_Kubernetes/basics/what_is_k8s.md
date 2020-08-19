---
title: "Create Azure Container Registry"
date: 2018-10-03T10:14:46-07:00
draft: false
weight: 30
---


Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0. Container Registry is private and hosted in Azure. You use it to build, store, and manage images for all types of container deployments.

Container images can be pushed and pulled with Container Registry by using the Docker CLI or the Azure CLI. You can use Azure portal integration to visually inspect the container images in the container registry. In distributed environments, the Container Registry geo-replication feature can be used to distribute container images to multiple Azure datacenters for localized distribution.

Azure Container Registry Tasks can also build container images in Azure. Tasks use a standard Dockerfile to create and store a container image in Azure Container Registry without the need for local Docker tooling. With Azure Container Registry Tasks, you can build on-demand or fully automate container image builds by using DevOps processes and tooling.

Let's deploy a container registry for the Fruit Smoothies environment.

1 - The container registry name must be unique within Azure and contain between 5 and 50 alphanumeric characters. For learning purposes, run this command from Azure Cloud Shell to create a Bash variable that holds a unique name.

```
ACR_NAME=acr$RANDOM

```
2 - You use the az acr create command to create the registry in the same resource group and region as your Azure Kubernetes Service (AKS) cluster. For example, aksworkshop in East US.

Run the command below to create the ACR instance.

```
az acr create \
    --resource-group $RESOURCE_GROUP \
    --location $REGION_NAME \
    --name $ACR_NAME \
    --sku Standard

```

You'll see a response similar to this JSON example when the command completes.

```
{
  "adminUserEnabled": false,
  "creationDate": "2019-12-28T01:33:23.906677+00:00",
  "id": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/aksworkshop/providers/Microsoft.ContainerRegistry/registries/acr4229",
  "location": "eastus",
  "loginServer": "acr4229.azurecr.io",
  "name": "acr4229",
  "networkRuleSet": null,
  "policies": {
    "quarantinePolicy": {
      "status": "disabled"
    },
    "retentionPolicy": {
      "days": 7,
      "lastUpdatedTime": "2019-12-28T01:33:25.070450+00:00",
      "status": "disabled"
    },
    "trustPolicy": {
      "status": "disabled",
      "type": "Notary"
    }
  },
  "provisioningState": "Succeeded",
  "resourceGroup": "aksworkshop",
  "sku": {
    "name": "Standard",
    "tier": "Standard"
  },
  "status": null,
  "storageAccount": null,
  "tags": {},
  "type": "Microsoft.ContainerRegistry/registries"
}

```

