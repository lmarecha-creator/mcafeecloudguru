---
title: "Create DevOps Project 2"
date: 2018-08-07T13:36:57-07:00
weight: 40
tags:
  - beginner
---

1- Sign in to Azure DevOps: https://azure.microsoft.com/en-gb/services/devops/


2 - Click on pipeline and create new pipeline to your code

![Azuredevops](/images/mfe/newpipeline.png?classes=border,shadow)

3 - Choose Github from the list

![Azuredevops](/images/mfe/gitcode.png?classes=border,shadow)

4 - Select Github ***Deployment of app with SQL*** repositry you have created in the previous lab

![Azuredevops](/images/mfe/selectrepo.png?classes=border,shadow)

5 - Select the starter pipeline

![Azuredevops](/images/mfe/starter-pipeline.png?classes=border,shadow)

6 -  Dwnoload azure-mvc-shiftleft-pipeline.yml from : https://github.com/MVCEBC/SQL-with-violation/blob/main/SQL-with-violation.zip
Copy pipeline code from (azure-mvc-shiftleft-pipeline.yml), make sure that indentation is correct. Click on Save and run, this commits pipeline yaml file to source code and executes pipeline. Make sure that file name matches to “azure-mvc-shiftleft-pipeline.yml”

![Azuredevops](/images/mfe/codepipeline-yaml.png?classes=border,shadow)

7- Make sure the file ***azure-mvc-shiftleft-pipeline.yml*** is visible on your Github repository

![Azuredevops](/images/mfe/github-yaml.png?classes=border,shadow)
#### You have successfully configured Azure DevOps projects to work with MVISION Cloud!  
