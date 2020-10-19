---
title: "MVISION Cloud & Azure DLP labs"
date: 2018-10-03T10:14:32-07:00
draft: false
weight: 90
tags:
  - AzureWorkshop2020
---
![DLP](/images/mfe/DLP_33532832_m.jpg?classes=border,shadow)

Azure storage is similar to a AWS S3 in that it is used to store data for various Azure services. Azure storage can store Binary Large Objects (BLOBs) which are basically files. BLOBs live in BLOB Containers (similar to S3 buckets).

>> _**A good introduction to Azure BLOB services can be found here**_ : https://www.red-gate.com/simple-talk/cloud/cloud-data/an-introduction-to-windows-azure-blob-storage/

MVISION Cloud can scan Azure Storage BLOB containers, just as we can for AWS S3 buckets.

## Pre-requisites:

1.  You have an **Azure account and Azure subscription** (can be pay-as-you-go)
2.  You have a **MVISION Cloud tenant** and the API is connected to Azure.
3.  You have completed the earlier Azure labs
4.  **StorageExplorer** is installed on your Mac / PC (You can download the software from https://azure.microsoft.com/en-us/features/storage-explorer/)
5.  You know how to create a MVISION Cloud DLP policy
6.  You know how to create an On Demand Scan

