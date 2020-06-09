---
title: "Container Vulnerability Assessment"
date: 2020-02-24
weight: 40
---

MVC also provides comprehensive CVE vulnerability assessment for Containers in registries!

For the sake of time, we will not be performing this portion in the lab today, but feel free to watch the short video below to see it in action.

<video width="100%" controls>
  <source src="/images/mvcscan/ContainerScanCVE.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

---
title: "LABS Course"
date: 2020-02-24
weight: 30
---

#### Prerequisites
> Cloud9 environment up and running : https://aws.amazon.com/cloud9/?nc1=h_ls
> Access to your AWS environment trough GUI : https://aws.amazon.com/?nc1=h_ls

#### LAB 1 - Build, Tag and Push a Docker Image to AWS ECR
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

#### LAB 2 - CVE Scan for your Docker Images stored in AWS ECR
#### LAB 3 - Fix the vulnerabilities found in the image (only for the 'wget' package)


#### Verify the binaries are in the path and executable
```
for command in kubectl jq envsubst
  do
    which $command &>/dev/null && echo "$command in path" || echo "$command NOT FOUND"
  done

```

From the above output, you are looking for 3 returns of "x in path".

#### Enable kubectl bash_completion
```
kubectl completion bash >>  ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion

```


### Configure Cloud9 Credential Management
{{% notice info %}}
Cloud9 normally manages IAM credentials dynamically. This isn't currently compatible with
the EKS IAM authentication, so we will disable it and rely on the IAM role instead.
{{% /notice %}}

- Return to your workspace and click the sprocket, or launch a new tab to open the Preferences tab
- Select **AWS SETTINGS**
- Turn off **AWS managed temporary credentials**
- Close the Preferences tab
![c9disableiam](/images/c9disableiam.png?classes=border,shadow)


To ensure temporary credentials aren't already in place we will also remove
any existing credentials file by executing the following command in the Terminal:
```
rm -vf ${HOME}/.aws/credentials
```

The final step ties your Cloud9 environment to the EKS Cluster

```
aws eks update-kubeconfig --name mcafee-workshop-eksctl --region us-west-2
```

This concludes the prep for the Kubernetes environment. We will return here after the scans to resolve some high severity incidents!
