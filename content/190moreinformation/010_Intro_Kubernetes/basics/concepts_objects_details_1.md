---
title: "Deploy the ratings front end"
date: 2018-10-03T10:15:55-07:00
draft: false
weight: 60
---

The Fruit Smoothies' ratings website consists of several components. There's a web frontend, a document database that stores captured data, and a RESTful ratings API that allows the web frontend to communicate with the database. The development team is using MongoDB as the document store database of choice for the ratings website.

In the previous unit, you deployed the ratings API. You'll continue your deployment and deploy the ratings web front end. The ratings web front end is a Node.js application. Recall that you've already created an Azure Container Registry instance. You used it to build a Docker image of the front end and store it in a repository.

In this exercise, you will:

Create a Kubernetes deployment for the web front end
Create a Kubernetes service manifest file to expose the web front end as a load-balanced service
Test the web front end

