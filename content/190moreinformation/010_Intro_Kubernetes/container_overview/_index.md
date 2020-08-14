---
title: "Application architecture"
date: 2018-10-03T10:14:32-07:00
draft: false
weight: 30
tags:
  
---

Our goal is to deploy an Azure managed Kubernetes service, Azure Kubernetes Service (AKS), that runs the Fruit Smoothies ratings website.

![AppArch](/images/mfe/app-arch.svg?classes=border,shadow)

There are several tasks that you'll complete to show how Kubernetes abstracts away complex container management and provides you with declarative configuration to orchestrate containers.

1 - Use AKS to deploy a Kubernetes cluster.

2 - Configure an Azure Container Registry to store application container images.

3 - Deploy the three ratings application components.

4 - Deploy the Fruit Smoothies website document database using Helm 3.

5 - Deploy the Fruit smoothies RESTFul API using deployment manifests.

6 - Deploy the Fruit smoothies website frontend using deployment manifests.

7 - Deploy Azure Kubernetes ingress using Helm 3.

8 - Configure SSL/TLS on the controller using cert-manager.

9 - Configure cluster autoscaler and horizontal pod autoscaler for the Fruit Smoothies cluster.



