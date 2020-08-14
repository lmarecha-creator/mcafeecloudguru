---
title: "Deploy Kubernetes with Azure Kubernetes Service"
date: 2018-10-03T10:14:32-07:00
draft: false
weight: 60
tags:
  
---

Fruit Smoothies wants to use Kubernetes as their compute platform. The development teams already use containers for application development and deployment, and using an orchestration platform will help them rapidly build, deliver, and scale their application.

To do this, you need to deploy the foundation of your Kubernetes environment.

In this exercise, you will:

- Create a new resource group.
- Configure cluster networking.
- Create an Azure Kubernetes Service cluster.
- Connect to the Kubernetes cluster by using kubectl.
- Create a Kubernetes namespace.

# Create a new resource group

You'll first need to create a resource group for your resources to deploy into.

1 - Sign in to Azure Cloud Shell with your Azure account. Select the Bash version of Cloud Shell [https://shell.azure.com/]

2 - We're going to reuse some values throughout the deployment scripts. For example, you need to choose a region where you want to create a resource group, such as East US. If you select a different value, remember it for the rest of the exercises in this module. You may need to redefine the value between Cloud Shell sessions. Run the following commands to record these values in Bash variables.

