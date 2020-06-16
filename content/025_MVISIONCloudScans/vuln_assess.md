---
title: "Container Vulnerability Assessment"
date: 2020-02-24
weight: 22
---

## Labs Description

MVISION Cloud Container Vulnerability Scan (CVS) assesses the vulnerability of container components. The scan evaluates the code embedded in containers at build time, and periodically after that, to make sure that known risks are exposed or mitigated to reduce the opportunities malicious actors have to exfiltrate a container workload.

Supported platforms include:

1. Amazon Elastic Container Registry (ECR)
2. API-based support for scanning manifest through ENS

## Labs Course

### *_Prerequisites_*
>> _**Cloud9 environment up and running**_ : https://aws.amazon.com/cloud9/?nc1=h_ls

>>***Access to your AWS environment trough GUI*** : https://aws.amazon.com/?nc1=h_ls

## LAB 1 - Build, Tag and Push a Docker Image to AWS ECR
**1#** Log on your AWS account and create an ECR (Container Images Registry) repository - Ex : "vulnerable-docker-images"

![ECR](/images/ECR-1.png?classes=border,shadow)

**2#** Log on your Cloud9 environment 

![ECR](/images/ECR-02.png?classes=border,shadow)

**3#** From Cloud9, retrieve YOUR authentication token and authenticate your Docker client to your registry by using the AWS CLI :

**NOTE : PLEASE USE YOUR OWN AWS ID ACCOUNT AND REGION where your ECR repo has been configured.**

Tip 1:

![ECR](/images/ECR-03.png?classes=border,shadow)

```
aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 686567285182.dkr.ecr.eu-central-1.amazonaws.com

```
**4#** Once successfully authenticated, import from the file ‘Dockerfile_to_fix’ docker config file in your Cloud9 environment

```
git clone https://github.com/lmarecha-creator/containers_CVE.git
```

**5#** **Wait for instruction** - Instructor to explain the Dockerfile structure

**6#** Build your Docker image using the following command (DO NOT FORGET THE ‘.’ AT THE END OF THE COMMAND – “dockerfile_to_fix” must be in lowercases):

```
docker build -t dockerfile_to_fix .
```
**7#** After the build completes, tag your image so you can push the image to this repository:

**NOTE : PLEASE USE YOUR OWN AWS ID ACCOUNT AND REGION where your ECR repo has been configured.**

```
docker tag dockerfile_to_fix:latest 686567285182.dkr.ecr.eu-central-1.amazonaws.com/vulnerable-docker-images:1
```
Tip 2: Same as Tip 1

**8#** Run the following command to push this image to your newly created AWS ECR repository:

**NOTE : PLEASE USE YOUR OWN AWS ID ACCOUNT AND REGION where your ECR repo has been configured.**

```
docker push 686567285182.dkr.ecr.eu-central-1.amazonaws.com/ vulnerable-docker-images:1
```
![ECR](/images/ECR-04.png?classes=border,shadow)

Tip 3: Same as Tip 1

**9#** Confirm that your Docker Image has correctly been pushed to your ECR :

![ECR](/images/ECR-05.png?classes=border,shadow)

## LAB 2 - CVE Scan for your Docker Images stored in AWS ECR

**1#**	Connect to https://auth.ui.mcafee.com/ and authenticate to MVision Cloud using your own account

**2#**	To enable CVEs Scan in Mvision Cloud, you must follow the Container Vulnerability Scan LAB in Mindtouch at https://success.myshn.net/MVISION_Cloud_Container_Security/MVISION_Cloud_Container_Security/Container_Vulnerability_Scan

**3#**	Run a Containers CVEs On-Demand Scan

**4#**	Review the incidents and confirm your see all the different CVE vulnerabilities

![ECR](/images/ECR-06.png?classes=border,shadow)

## LAB 3 - Fix the vulnerabilities found in the image (only for the 'wget' package)

**1#**	From your Cloud9 environment, edit the file “Dockerfile_to_fix” and find the line in relation with the incident reported in MVC during the previous scan (wget)

**2#**	Mvision Cloud tells you what version of wget fixes this vulnerability – Make the appropriate change in the code

**NOTE : Ping your instructor if stuck - This is the most difficult (or less easy) part of the Lab**

**3#**	Build again the new docker image

```
docker build -t dockerfile_to_fix .
```
**4#**	Tag again the docker image (use '2' for exemple) :

docker tag dockerfile_to_fix:latest 686567285182.dkr.ecr.eu-central-1.amazonaws.com/vulnerable-docker-images:2

**5#**	Push the v2 image to ECR :

```
docker push 686567285182.dkr.ecr.eu-central-1.amazonaws.com/vulnerable-docker-images:2
```
**6#**	Run a Containers CVEs On-Demand Scan

**7#**	Review the incidents and confirm there is not anymore CVEs reported for WGET. It confirms you successfully fixed the vulnerability.


**Labs completed, Congratz !**



