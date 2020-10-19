---
title: "Create and Configure a Blob Storage"
date: 2018-10-03T10:23:24-07:00
draft: false
weight: 130
---

## LAB 1

1#  Connect to https://portal.azure.com using your admin credentials

2#  Launch Cloud Shell from the top navigation of the Azure portal

![IDE](/images/mfe/shell-icon.png?classes=border,shadow)

3#  Select a subscription to create a storage account and Microsoft Azure Files share.

4#  Select "Create storage".

5#  Check that the environment drop-down from the left-hand side of shell window says Bash. 

![IDE](/images/mfe/env-selector.png?classes=border,shadow)

6#  List subscriptions you have access to.

```
az account list
```
7#  List subscriptions you have access to.

```
az account set --subscription 'my-subscription-name'
```
8# Create a resource group using the following command. Make sure to **replace the resource group name and location with your deployment preference**.

```
az group create --name LaurentLab-ressource-group --location westus
```

9# Create Azure storage account using the following command:

```
az storage account create --name <account-name> --resource-group <resource group name> --location <azure region> --sku <storage account sku> --kind <storage account sku>
```
 **Update the values as follows**

    a. Name: Name of the storage account
    b. Resource group: Give the name of resource group created above in Step 8.
    c. Location: Update with the name of the Azure region. Output values from the following command can be used here #az account list-locations
    d. SKU: Select from the following SKUs based on storage replication requirements: Premium_LRS, Premium_ZRS, Standard_GRS, Standard_GZRS, Standard_LRS,          Standard_RAGRS, Standard_RAGZRS, Standard_ZRS
    e. Kind: Select the storage account type from the following options: BlobStorage, BlockBlobStorage, FileStorage, Storage, StorageV2
