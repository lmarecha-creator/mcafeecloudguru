---
title: "Deploy MongoDB"
date: 2018-10-03T10:15:55-07:00
draft: false
weight: 40
---

The Fruit Smoothies' ratings website consists of several components. There's a web frontend, a document database that stores captured data, and a RESTful API that allows the web frontend to communicate with the database. The development team is using MongoDB as the document store database of choice for the ratings website.

In this exercise, you'll deploy MongoDB to the Azure Kubernetes Service (AKS) cluster using Helm. You'll also see how to use a Kubernetes secret to store the MongoDB connection username and password.

This example architecture deploys MongoDB on the cluster for the application to use to store data. While this is acceptable for test and development environments, it's not recommended for production environments. For production, it's recommended to store your application state and data in a scalable data storage platform, such as CosmosDB.

In this exercise, you will:

Configure the Helm stable repository
Install the MongoDB chart
Create a Kubernetes secret to hold database credentials

![AzureK8ssrv](/images/mfe/azurek8s-service.svg?classes=border,shadow)

#### Add the Helm bitnami repository

Helm is an application package manager for Kubernetes. It offers a way to easily deploy applications and services using charts.

The Helm client is already installed in the Azure Cloud Shell and can be run with the helm command. Helm provides a standard repository of charts for many different software packages. Helm has a chart for MongoDB that is part of the official Helm bitnami charts repository.

1 - Configure the Helm client to use the stable repository by running the helm repo add command below.

helm repo add bitnami https://charts.bitnami.com/bitnami
