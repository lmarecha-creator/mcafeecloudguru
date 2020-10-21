---
title: "Near Real Time DLP Scan"
date: 2020-02-24
weight: 70
---

MVISION Cloud Near Real Time DLP for Azure is another milestone in keep our clients safe from malware or loss of critical data disrupting our clients businesses.

Purpose
This lab will help you walk through the setup of **NRT DLP for Azure**.

Prerequisites
1. Must have an Azure account and MVISION Cloud tenant already configured

2. Setup Azure Blob Storage

3. Access to the demo files

4. Optional Azure CLI

## Setup Permissions

In Azure Cloud Sehll CLI, run these two commands: 

The assignee is the username used to enable your Azure tenant in MVISION Cloud.

#1 Retreive your Azure Subscription ID by running the following command - **Make sure it reflects your own environment**

```
az account list
```

![AzureSub](/images/mfe/azuresub.png?classes=border,shadow)

az role assignment create --role "Reader and Data Access" --assignee accountname@mcafeetmecom.onmicrosoft.com --subscription df03f283-1111-4444-8180-22222222222

Get your Azure subscription ID: az account list --output table :

az role assignment create --role "Reader" --assignee accountname@mcafeetmecom.onmicrosoft.com --subscription df03f283-1111-4444-8180-222222222222

or use the UI

1. Navigate to portal.azure.com and log in

2. Search for Subscription
