---
title: "Connect to your AWS account"
date: 2018-08-07T08:30:11-07:00
weight: 10
draft: false
tags:
  - mfesesummit2020
  
---

When logged in to your AWS account, navigate to services and type cloudformtion:

![CF](/images/mfe/CF.png?classes=border,shadow)

Please follow the below steps for integrating AWS Ci/CD tools with McAfee MVISION Shift left inline

Navigate to AWS Cloudformation page and select Create stack -> With new resources (standard). The user will be navigated to Create stack page as shown below.

![CF2](/images/mfe/CF2.png?classes=border,shadow)

Upload the shift-left-aws-mvision.yaml cloud formation and select Next. The user will be navigated to Specify stack details page as shown below.

![CF3](/images/mfe/CF3.png?classes=border,shadow)

{{% notice Important %}}
Ensure you are not using HTTPS, some browsers will default to this.  If you wish to secure your Jenkins instance later by following the instructions [from the Jenkins Wiki.](https://wiki.jenkins.io/pages/viewpage.action?pageId=135468777)
{{% /notice %}}

## Login to Jenkins

Use the following credentials to login to your Jenkins instance:

  Username: **admin**
  Password: **McAfee123!**

You should be presented with a Jenkins home screen similar to the one below:

![Jenkins Signin](/images/mfe/jenkinshome.png?classes=border,shadow)

#### Continue to the next section to start configuring Jenkins
