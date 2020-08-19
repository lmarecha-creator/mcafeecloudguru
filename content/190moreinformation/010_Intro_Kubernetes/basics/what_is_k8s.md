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

