---
title: "Container Vulnerability Assessment"
date: 2020-02-24
weight: 40
---

# LABS Description
## *_Introduction_*

MVISION Cloud Container Vulnerability Scan (CVS) assesses the vulnerability of container components. The scan evaluates the code embedded in containers at build time, and periodically after that, to make sure that known risks are exposed or mitigated to reduce the opportunities malicious actors have to exfiltrate a container workload.

Supported platforms include:

1. Amazon Elastic Container Registry (ECR)
2. API-based support for scanning manifest through ENS

# LABS Course
## Prerequisites
1. Cloud9 environment up and running : https://aws.amazon.com/cloud9/?nc1=h_ls
2. Access to your AWS environment trough GUI : https://aws.amazon.com/?nc1=h_ls

## LAB 1 - Build, Tag and Push a Docker Image to AWS ECR
1. Log on your AWS account and create an ECR (Container Images Registry) repository - Ex : "vulnerable-docker-images"
2. Log on your Cloud9 environment 
3. From Cloud9, retrieve YOUR authentication token and authenticate your Docker client to your registry by using the AWS CLI :

Note : PLEASE USE YOUR OWN AWS ID ACCOUNT AND REGION where your ECR repo has been configured.

```
aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 686567285182.dkr.ecr.eu-central-1.amazonaws.com

```
4. Once successfully authenticated, import from [] the file ‘Dockerfile_to_fix’ docker config file in your Cloud9 environment

5. <Wait for instruction> - Instructor to explain the Dockerfile structure

6. Build your Docker image using the following command (DO NOT FORGET THE ‘.’ AT THE END OF THE COMMAND – “dockerfile_to_fix” must be in lowercases):

```
docker build -t dockerfile_to_fix .
```
7. After the build completes, tag your image so you can push the image to this repository:

Note : PLEASE USE YOUR OWN AWS ID ACCOUNT AND REGION where your ECR repo has been configured.
```
docker tag dockerfile_to_fix:latest 686567285182.dkr.ecr.eu-central-1.amazonaws.com/ vulnerable-docker-images:1
```
8.Run the following command to push this image to your newly created AWS ECR repository:

Note : PLEASE USE YOUR OWN AWS ID ACCOUNT AND REGION where your ECR repo has been configured.
```
docker push 686567285182.dkr.ecr.eu-central-1.amazonaws.com/ vulnerable-docker-images:v1
```

## LAB 2 - CVE Scan for your Docker Images stored in AWS ECR
## LAB 3 - Fix the vulnerabilities found in the image (only for the 'wget' package)
