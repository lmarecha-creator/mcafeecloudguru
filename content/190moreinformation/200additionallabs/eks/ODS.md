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

#1 Retreive your Azure Subscription ID by running the following command 

```
az account list
```

![AzureSub](/images/mfe/azuresub.png?classes=border,shadow)

#2 run these two commands to create a role and assign it to your account - **Make sure to replace the values by your own account and subscription ID : 
```
az role assignment create --role "Reader and Data Access" --assignee accountname@mcafeetmecom.onmicrosoft.com --subscription df03f283-1111-4444-8180-22222222222
```

![AzureSub](/images/mfe/azuresub2.png?classes=border,shadow)

```
az role assignment create --role "Reader" --assignee accountname@mcafeetmecom.onmicrosoft.com --subscription df03f283-1111-4444-8180-222222222222
```

![AzureSub](/images/mfe/azuresub3.png?classes=border,shadow)

## Setup WebHook

These steps help you configure **Azure Event Grid** Subscription with Webhook

#1. Log into the Azure Portal

#2. Navigate to Templates

![AzureSub](/images/mfe/hook1.png?classes=border,shadow)


