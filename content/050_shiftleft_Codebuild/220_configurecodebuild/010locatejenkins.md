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

1. Navigate to AWS Cloudformation page and select Create stack -> With new resources (standard). The user will be navigated to Create stack page as shown below.

![CF2](/images/mfe/CF2.png?classes=border,shadow)

Upload the shift-left-aws-mvision.yaml cloud formation and select Next. The user will be navigated to Specify stack details page as shown below.

![CF3](/images/mfe/CF3.png?classes=border,shadow)

3. Enter the stack name and Click Next. The user will be navigated to the Configure stack options page.
4. Click Next and the user will be navigated to the review page.
5. In the review page, select the checkbox against I acknowledge that AWS CloudFormation might create IAM resources with custom names and click Create Stack.
6. Make sure the stack creation is complete with status CREATE_COMPLETE.
7. Download the buildspec.yml
8. Navigate to the AWS CodeCommit page, select the repo shift-left-repo. Inside the repo select Add file --> Upload file and upload the file download from step7, provide Author Name, Email address and click Commit changes.
9. Once the file is committed, navigate to the AWS Systems Manager. The user will be navigated to the AWS Systems Manager page. Select the Parameter Store from the left menu.
10. Click Create parameter, the user will be navigated to the Parameter details page as shown below. Populate the below values. Make sure the parameters are created in the same region as the repository and code build. Use Type 'SecureString'.
 - Name with /codebuild/mvision_username and enter the MVISION username in the value text area and click Create Parameter.
 - Name with /codebuild/mvision_password and enter the MVISION password in the value text area and click Create Parameter.

![SM](/images/mfe/SM.png?classes=border,shadow)


11-  Navigate to the AWS Lambda page, select the lambda function invoke-code-build-<<account_id>>. The user will be navigated to the lambda function.
12-  In the Configuration tab, click on Add trigger. The user will be navigated to the Add trigger page as shown below.

![Lambda](/images/mfe/Lambda.png?classes=border,shadow)

13- Select CodeCommit as the trigger, select the repository name as shift-left-repo, provide a name for the trigger, select Push to existing branch from Events drop-down, select master in the Branch names drop-down and Click on Add.


![Lambda2](/images/mfe/Lambda2.png?classes=border,shadow)
