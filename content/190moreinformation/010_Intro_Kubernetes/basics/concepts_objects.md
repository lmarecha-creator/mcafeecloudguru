---
title: "Deploy the ratings API"
date: 2018-10-03T10:15:55-07:00
draft: false
weight: 50
---

The Fruit Smoothies' ratings website consists of several components. There's a web frontend, a document database that stores captured data, and a RESTful ratings API that allows the web frontend to communicate with the database. The development team is using MongoDB as the document store database of choice for the ratings website.

In the previous unit, you deployed MongoDB using Helm. You'll continue your deployment and deploy the ratings API. The ratings API is a Node.js application written by using the Express framework. It stores and retrieves items and their ratings in a MongoDB database. Recall that you already created an Azure Container Registry instance.

In this exercise, you will:

Create a Kubernetes deployment for the RESTful API
Create a Kubernetes service to expose the RESTful API over the network

