---
title: "Create DevOps Project"
date: 2018-08-07T13:36:57-07:00
weight: 30
tags:
  - beginner
---

1- Sign in to Azure DevOps: https://azure.microsoft.com/en-gb/services/devops/

![Azuredevops](/images/mfe/AzureDevOps.png?classes=border,shadow)

2- Create a new project in Azure DevOps

![Azuredevops](/images/mfe/devops-project.png?classes=border,shadow)

3- Provide a name and click on create

![Azuredevops](/images/mfe/new-project.png?classes=border,shadow)

4- Click on Pipelines, Create Variable group under Library with name “MVISION_GROUP”

5- Create below variables with MVISION account details

  - MVISION_USERNAME (tenant login)
  - MVISION_PASSWORD( tenant password, Mark this variable type to secret)
  - ENVIRONMENT ( MVISION URL : https://www.myshn.net/)
  - CLOUD_SERVICE_PROVIDER ( Template types: Azure ) 

![Azuredevops](/images/mfe/variable2.png?classes=border,shadow)

6- Create pipeline to your code

![Azuredevops](/images/mfe/newpipeline.png?classes=border,shadow)

7- Choose Github from the list

![Azuredevops](/images/mfe/gitcode.png?classes=border,shadow)

8- Select Github repositry you have created in the previous lab

![Azuredevops](/images/mfe/selectrepo.png?classes=border,shadow)

9- Select the starter pipeline

![Azuredevops](/images/mfe/starter-pipeline.png?classes=border,shadow)

10-  Dwnoload azure-mvc-shiftleft-pipeline.yml from : https://github.com/MVCEBC/shift-left-yaml/blob/main/azure-mvc-shiftleft-pipeline.yml.zip
Copy pipeline code from (azure-mvc-shiftleft-pipeline.yml), make sure that indentation is correct. Click on Save and run, this commits pipeline yaml file to source code and executes pipeline. Make sure that file name matches to “azure-mvc-shiftleft-pipeline.yml”

![Azuredevops](/images/mfe/codepipeline-yaml.png?classes=border,shadow)

11- Make sure taht  ***azure-mvc-shiftleft-pipeline.yml*** is visible on your Github repository

![Azuredevops](/images/mfe/github-yaml.png?classes=border,shadow)
#### You have successfully configured Azure DevOps projects to work with MVISION Cloud!  Please move on to the next section to configure MVISION Cloud policies.
