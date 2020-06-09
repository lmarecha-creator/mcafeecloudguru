---
title: "What is Codebuid?"
date: 2018-08-07T08:30:11-07:00
weight: 10
draft: false
tags:
  - mfesesummit2020
  
---

## Introducing Jenkins

AWS CodeBuild is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy. With CodeBuild, you don’t need to provision, manage, and scale your own build servers. CodeBuild scales continuously and processes multiple builds concurrently, so your builds are not left waiting in a queue. You can get started quickly by using prepackaged build environments, or you can create custom build environments that use your own build tools. With CodeBuild, you are charged by the minute for the compute resources you use.
![What_is_Jenkins](/images/mfe/CICD-Jenkins.png?classes=border,shadow)

As shown above, once code is checked into a repository (such as AWS CodeCommit) it is ready to be built by Jenkins.  This build can be triggered automatically, on a schedule, or manually as part of a project.  Each project in Jenkins contains a series of build steps and triggers.  For example, a simple containerized application might look like this:

  1.  Build triggered by code update, timer, or by clicking the "build now" button
  2.  The latest source code is pulled from the code repository (AWS CodeCommit)
  3.  Execute build scripts, compile code and test code
  4.  Deploy IaaS templates (such as EC2 instances, security groups, load balancers, etc.)
  5.  Configure the container orchestrator (such as Kubernetes)
  5.  Deploy code into the new infrastructure
  6.  Run test scripts against the new infrastructure and code
  7.  Modify DNS to move users over to the newly deployed infrastructure and code

These builds generally take only a few minutes, allowing errors and failures to be addressed by developers quickly.  This speedy and automatic feedback drives huge amount of efficiency for developers.

#### Move on to the next section to learn more about how MVISION Cloud integrates with Jenkins