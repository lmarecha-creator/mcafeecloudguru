---
title: "Create and Configure a Blob Storage"
date: 2018-10-03T10:23:24-07:00
draft: false
weight: 130
---

## LAB 1

1.  Connect to https://portal.azure.com using your admin credentials
2.  Launch Cloud Shell from the top navigation of the Azure portal

![IDE](/images/mfe/shell-icon.png?classes=border,shadow)

3.  Select a subscription to create a storage account and Microsoft Azure Files share.
4.  Select "Create storage".
5.  Check that the environment drop-down from the left-hand side of shell window says Bash. 

![IDE](/images/mfe/env-selector.png?classes=border,shadow)

6.  List subscriptions you have access to.

```
az account list
```
7.  List subscriptions you have access to.

```
az account set --subscription 'my-subscription-name'
```
