---
title: "Lab 1 - Easy"
chapter: false
weight: 10
tags:
  - beginner
  - shiftleft
  
---
## Easy difficulty

We're going to start with VM ARM based template

1. Download deployment files of a Windows VM from this link :  https://github.com/MVCEBC/ARM-Windows-VM-/blob/main/101-vm-simple-windows.zip

2. Log into your Github and select the repository you have created in the previous lab : https://github.com/

3. Extract the files and upload them to your repository. Make sure you have all files inclding “azure-mvc-shiftleft-pipeline.yml”

  ![Build Project 1](/images/mfe/arm-vm.png?classes=border,shadow)
  
4. Open your Azure DevOps console  https://azure.microsoft.com/en-gb/services/devops/  and click on Pipelines

  ![Pipeline](/images/mfe/pipeline.png?classes=border,shadow)
  
5. Double click on the build you have created before and click again 

![Click Failed Build](/images/mfe/pipeline2.png?classes=border,shadow)

![Click Failed Build](/images/mfe/pipeline3.png?classes=border,shadow)

![Click Failed Build](/images/mfe/pipeline4.png?classes=border,shadow)
  
6.  The build will fail.  Let's click the number next to the red dot of the recent build to explore why:

    
7.  From the build status screen, click MVISION Template Auditing "Console Output":

 ![Click Failed Build](/images/mfe/pipeline5.png?classes=border,shadow)
  
6.  Investigate the cause of the build failure from the console output:

  ![Investigate](/images/mfe/project1consoleoutput.png?classes=border,shadow)
  
7.  Back in Github, expand the "repository" and double click the "azuredeploy.json" file to open it and then click on edit on the right corner

  ![Open Easy Cloudformation File](/images/mfe/arm-failed.png?classes=border,shadow)
  
  ![Open Easy Cloudformation File](/images/mfe/git-edit.png?classes=border,shadow)
  
8.  Using the information in the failed DevOps console output, try to find and fix the problem within the ARM template.  Feel free to use Google and Azur Documentation to assist with making the necessary changes! 

9.  When you are satisfied with your changes, click on commit changes to your repository.

![Git commit and push](/images/mfe/commit-change.png?classes=border,shadow)

  
10. Go back to Azure DevOps to see if the new build was successful.

12. If not, then investigate why it failed, try fix the issue check in the code changes again, and investigate the next build!


