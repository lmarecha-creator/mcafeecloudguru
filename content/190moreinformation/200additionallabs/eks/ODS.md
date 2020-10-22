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

#2 run these two commands to create a role and assign it to your account - **Make sure to replace the values by your own account and subscription ID** : 
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

#3. Select **Add**

![AzureSub](/images/mfe/hook2.png?classes=border,shadow)

#4. Add General info as seen here and select Ok.

![AzureSub](/images/mfe/hook3.png?classes=border,shadow)

#5. **Copy** paste the content of this file: update_Storage_account_with_Event_sub.json from https://github.com/lmarecha-creator/DLP_Workshop/blob/main/update_Storage_account_with_Event_sub.json into the Arm Template page, then **select ok**, then **add**

FYI : Using this template will help minimize the time it takes to enable Event Subscription across all blobs.

![AzureSub](/images/mfe/hook4.png?classes=border,shadow)

#6. This will be the outcome:

![AzureSub](/images/mfe/hook5.png?classes=border,shadow)

#7. Deploy the template

![AzureSub](/images/mfe/hook6.png?classes=border,shadow)

#8. Fill in the required information. 

**Your storage name and endpoint will be different than what is shown in the image below.**


>> Note: The storage name field in the deployment template is a JSON formatted array of strings, the strings contain the Azure storage accounts that you want to subscribe for events which will then be sent to MVISION Cloud via webhooks, ie: this field determines which storage accounts you want to monitor for NRT DLP.

Eg: Customer has 3 storage accounts named "blobaccount", "customerfiles" & "devblobs" then the storage name field should contain:

["blobaccount", "customerfiles", "devblobs"] <<

