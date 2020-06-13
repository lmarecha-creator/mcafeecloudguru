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

How CodeBuild works?

The following diagram shows what happens when you run a build with CodeBuild:

![codebuild-flow](/images/mfe/codebuild-flow.png?classes=border,shadow)

1- As input, you must provide CodeBuild with a build project. A build project includes information about how to run a build, including where to get the source code, which build environment to use, which build commands to run, and where to store the build output. A build environment represents a combination of operating system, programming language runtime, and tools that CodeBuild uses to run a build. For more information, see:



2- CodeBuild uses the build project to create the build environment.

3- CodeBuild downloads the source code into the build environment and then uses the build specification (buildspec), as defined in the build project or included directly in the source code. A buildspec is a collection of build commands and related settings, in YAML format, that CodeBuild uses to run a build. For more information, see the Buildspec reference.

4- If there is any build output, the build environment uploads its output to an S3 bucket. The build environment can also perform tasks that you specify in the buildspec (for example, sending build notifications to an Amazon SNS topic). For an example, see Build notifications sample.

5- While the build is running, the build environment sends information to CodeBuild and Amazon CloudWatch Logs.

6- While the build is running, you can use the AWS CodeBuild console, AWS CLI, or AWS SDKs to get summarized build information from CodeBuild and detailed build information from Amazon CloudWatch Logs. If you use AWS CodePipeline to run builds, you can get limited build information from CodePipeline.


Here’s a reference architecture that puts these components together to deliver a continuous deployment pipeline of Docker applications onto ECS:

![codebuild](/images/mfe/codebuild.png?classes=border,shadow)




#### Move on to the next section to learn more about how MVISION Cloud integrates with CodeBuild
