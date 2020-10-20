---
title: "Create and Configure a Blob Storage"
date: 2018-10-03T10:23:24-07:00
draft: false
weight: 130
---

## LAB 1

**1#**  Connect to https://portal.azure.com using your admin credentials

**2#**  Launch Cloud Shell from the top navigation of the Azure portal

![IDE](/images/mfe/shell-icon.png?classes=border,shadow)

**3#**  Select a subscription to create a storage account and Microsoft Azure Files share (if asked).

**4#**  Select "Create storage" (if asked).

**5#**  Check that the environment drop-down from the left-hand side of shell window says Bash. 

![IDE](/images/mfe/env-selector.png?classes=border,shadow)

**6#**  List subscriptions you have access to.

```
az account list
```
**7#**  List subscriptions you have access to.

```
az account set --subscription 'my-subscription-name'
```
**8#** Create a resource group using the following command. Make sure to **replace the resource group name and location with your deployment preference**.

```
az group create --name LaurentLab-ressource-group --location westus
```

**9#** Create Azure storage account using the following command - **Make sure the parameters reflect your own environment** - :

```
az storage account create --name laurentlab --resource-group LaurentLab-ressource-group --location westus --sku Standard_LRS --kind StorageV2
```

. **Name**: Name of the storage account - Whatever you like

. **Resource group**: Give the name of resource group created above in Step 2.

. **Location**: Use 'westus'

. **SKU**: Select 'Standard_LRS'

. **Kind**: Select 'StorageV2'

**10#** You can list the  storage accounts in the resource group to view the newly provisioned storage using the following command:

```
#az storage account list -g <resource group name>
```

![BLOB](/images/mfe/AZ_blob.png?classes=border,shadow)
