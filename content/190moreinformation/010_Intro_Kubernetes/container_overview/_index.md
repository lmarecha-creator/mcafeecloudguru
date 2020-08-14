---
title: "Application architecture"
date: 2018-10-03T10:14:32-07:00
draft: false
weight: 30
tags:
  
---

Our goal is to deploy an Azure managed Kubernetes service, Azure Kubernetes Service (AKS), that runs the Fruit Smoothies ratings website.



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



## 2) What is Docker?

A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.&#160;Container images become containers at runtime and in the case of Docker containers - images become containers when they run on [Docker Engine](https://www.docker.com/products/docker-engine)

![dockers](/images/mfe/docker.png?classes=border,shadow)


## 3) What is Kubernetes?

<a href="https://kubernetes.io/">Kubernetes</a>&#160;is an open source platform for managing containerized applications. If you use Docker to deploy&#160;an application, a Kubernetes cluster can manage your servers and deployments, including tasks such as scaling, deployment, and rolling upgrades.

* **Nodes**:
A Kubernetes cluster consists of at least one **Master** node and several **Worker** nodes. The master node runs the API server, the scheduler and the controller manager, and the actual application is deployed dynamically across the cluster.

* **Pods** A <a href="https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/">Pod</a>&#160;is a group of one or more tightly coupled containers that share resources such as storage and network. Containers inside a pod are started, stopped, and replicated as a group.

![podss](/images/mfe/pods.png?classes=border,shadow)

## 4) What is EKS?

Amazon Elastic Kubernetes Service (EKS) is a managed&#160;<a href="https://aws.amazon.com/kubernetes/" target="_blank">Kubernetes</a>&#160;service that makes it easy for you to run Kubernetes on AWS without needing to install, operate, and maintain your own Kubernetes control plane.&#160;Amazon EKS automatically manages the availability and scalability of the Kubernetes control plane nodes that are responsible for starting and stopping&#160;<a href="https://aws.amazon.com/containers/" target="_blank">containers</a>, scheduling containers on virtual machines, storing cluster data, and other tasks. Amazon EKS automatically detects and replaces unhealthy control plane nodes for each cluster.

![ekss](/images/mfe/eks.png?classes=border,shadow)

## 5) What does MVision Cloud for Containers provide for Container Security?

MVISION Cloud Container Security provides&#160;Cloud Security Posture Management (CSPM) for major IaaS providers such as Amazon Web Services (AWS), as part of a unified cloud security platform. This has been extended and enhanced to&#160;secure dynamic container workloads and the&#160;infrastructure they depend on.&#160;

MVISION Cloud Container Security solution continuously checks CIS Level 1 and 2 benchmark requirements to detect and correct any misconfigurations or drift in workloads and containers.&#160;Currently, MVISION Cloud Container Security supports Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS), and provides more than 78 preconfigured <a href="https://success.myshn.net/MVISION_Cloud_Container_Security/MVISION_Cloud_Container_Security/Policy_Templates_for_Container_Security"> Policy Templates </a> (46 for EKS and 32 for ECS)

For EKS, as of the MVISION Cloud 4.4.0 release, MCC supports CSPM audit of only the **Master** node, **NOT** the Worker nodes


## 6) What is ECS?

Amazon Elastic Container Service (Amazon ECS) is a fully managed container orchestration service. You can choose to run your ECS clusters using <a href="https://aws.amazon.com/fargate/">AWS Fargate</a>, which is serverless compute for containers. Fargate removes the need to provision and manage servers, lets you specify and pay for resources per application, and improves security through application isolation by design.&#160;

![ecss](/images/mfe/ecs.png?classes=border,shadow)
