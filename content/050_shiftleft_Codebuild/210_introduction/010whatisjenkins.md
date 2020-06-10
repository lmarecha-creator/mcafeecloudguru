---
title: "What is AWS Codebuild?"
date: 2018-08-07T08:30:11-07:00
weight: 10
draft: false
tags:
  - mfesesummit2020
  
---

## Introducing AWS CodeBuild

AWS CodeBuild is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy. With CodeBuild, you don’t need to provision, manage, and scale your own build servers. CodeBuild scales continuously and processes multiple builds concurrently, so your builds are not left waiting in a queue. You can get started quickly by using prepackaged build environments, or you can create custom build environments that use your own build tools. With CodeBuild, you are charged by the minute for the compute resources you use.
You use AWS CodeBuild to build a collection of sample source code input files (build input artifacts or build input) into a deployable version of the source code (build output artifact or build output). Specifically, you instruct CodeBuild to use Apache Maven, a common build tool, to build a set of Java class files into a Java Archive (JAR) file. You do not need to be familiar with Apache Maven or Java.

CodeBuild provides these benefits:

Fully managed – CodeBuild eliminates the need to set up, patch, update, and manage your own build servers.

On demand – CodeBuild scales on demand to meet your build needs. You pay only for the number of build minutes you consume.

Out of the box – CodeBuild provides preconfigured build environments for the most popular programming languages. All you need to do is point to your build script to start your first build.

As the following diagram shows, you can add CodeBuild as a build or test action to the build or test stage of a pipeline in AWS CodePipeline. AWS CodePipeline is a continuous delivery service that you can use to model, visualize, and automate the steps required to release your code. This includes building your code. A pipeline is a workflow construct that describes how code changes go through a release process.

![codepipeline](/images/mfe/codepipeline.png?classes=border,shadow)


Here’s a reference architecture that puts these components together to deliver a continuous deployment pipeline of Docker applications onto ECS:

![codebuild](/images/mfe/codebuild.png?classes=border,shadow)




#### Move on to the next section to learn more about how MVISION Cloud integrates with CodeBuild
