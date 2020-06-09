---
title: "About the MVISION Cloud & AWS CodeBuild Integration"
date: 2018-08-07T08:30:11-07:00
weight: 20
draft: false
tags:
  - mfesesummit2020
  
---

## About Shift Left Inline integration with AWS CodeCommit and CodeBuild

McAfee MVISION Cloud provides a security solution to evaluate the DevOps templates both in offline and inline mode. Using inline mode, you can integrate your repository and CI/CD tools with Shift left inline APIs which MVISION provides to check for the security vulnerabilities present in the DevOps template file. Currently, the MVISION cloud supports the evaluation of DevOps templates of AWS and Azure including terraform support for both AWS & Azure. In this illustration, we've integrated shift left with Bitbucket's own CI/CD tool, Bitbucket pipelines.

When enables as part of a project, AWS CodeBuild calls an MVISION Cloud API to check any infrastructure-as-code (such as a CloudFormation template) for compliance with policies enabled in the MVISION Cloud Dashboard.  If any deviations are present, CodeBuild will stop the build and output a discription of the problem (such leaving wide SSH open) to the build/console log.

![MVC-codebuild](/images/mfe/MVC-codebuild.png?classes=border,shadow)

The project now has a new build step:

  1.  Build triggered by code update in AWS CodeCommit repository
  2.  The latest source code is pulled from the code repository (AWS CodeCommit)
  3.  <b><span style="color:red">Infrastructure-as-Code (CloudFormation templates) are checked by MVISION Cloud</span></b>
  4.  Execute build scripts, compile code and test code
  5.  Deploy IaaS templates (such as EC2 instances, security groups, load balancers, etc.)
  6.  Configure the container orchestrator (such as Kubernetes)
  7.  Deploy code into the new infrastructure
  8.  Run test scripts against the new infrastructure and code
  9.  Modify DNS to move users over to the newly deployed infrastructure and code

If non-compliant infrastructure templates are identified, developers receive immediate feedback on the problem:

![codebuild-violation](/images/mfe/codebuild-violation.png?classes=border,shadow)


#### Continue to the next section for a summary of our lab environment and CI/CD pipeline. 
