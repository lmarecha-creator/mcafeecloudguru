---
title: "Lab 1 - Easy"
chapter: false
weight: 5
tags:
  - beginner
  - shiftleft
  
---
## Easy difficulty

We're going to start with VM ARM based template


1. Log into your Github and select the repository you have created in the previous lab : https://github.com/

2. Make sure you have all files including “azure-mvc-shiftleft-pipeline.yml”

  ![Build Project 1](/images/mfe/arm-vm.png?classes=border,shadow)
  
3. Open your Azure DevOps console  https://azure.microsoft.com/en-gb/services/devops/  and click on Pipelines

  ![Pipeline](/images/mfe/pipeline.png?classes=border,shadow)
  
4. Double click on the build you have created before and then click again 

![Click Failed Build](/images/mfe/pipeline6.png?classes=border,shadow)

![Click Failed Build](/images/mfe/pipeline3.png?classes=border,shadow)

![Click Failed Build](/images/mfe/pipeline4.png?classes=border,shadow)
  
5. The build will fail.  Let's click the number next to the red dot of the recent build to explore why:

    
6. From the build status screen, click MVISION Template Auditing "Console Output":

 ![Click Failed Build](/images/mfe/pipeline5.png?classes=border,shadow)
  
7. Investigate the cause of the build failure from the console output:

  ![Investigate](/images/mfe/violation1.png?classes=border,shadow)
  
8. Back in Github, expand the "repository" and double click the "azuredeploy.json" file to open it and then click on edit on the right corner

  ![Open Easy Cloudformation File](/images/mfe/arm-failed.png?classes=border,shadow)
  
  ![Open Easy Cloudformation File](/images/mfe/git-edit.png?classes=border,shadow)
  
9. Using the information in the failed DevOps console output, try to find and fix the problem within the ARM template.  Feel free to use Google and Azur Documentation to assist with making the necessary changes! 

10. When you are satisfied with your changes, click on commit changes to your repository.

![Git commit and push](/images/mfe/commit-change.png?classes=border,shadow)

  
11. Go back to Azure DevOps to see if the new build was successful.

12. If not, then investigate why it failed, try fix the issue check in the code changes again, and investigate the next build!


