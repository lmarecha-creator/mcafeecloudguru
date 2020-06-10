---
title: "Configure CodeBuild Projects"
date: 2018-08-07T08:30:11-07:00
weight: 20
draft: false
tags:
  - mfesesummit2020
  
---

Now the integration of CodeCommit & CodeBuild with McAfee MVISION Cloud shift left inline API is done, the final step is to enable the security checks are part of the project's build process.

To get started, return to your CodeCommit and copy repository by clicking on clone https

![CC-repo](/images/mfe/CC-repo.png?classes=border,shadow)

Clone a CodeCommit Repository into your AWS Cloud9 Development Environment. In the terminal, run the git clone command, specifying the HTTPS clone URL of your repository. For example, if you want to clone a repository named shift-left-repo in the US East (Ohio) Region, you would enter:

git clone https://git-codecommit.us-east-2.amazonaws.com/v1/repos/Shift-left-repo

You can find the Clone URL for your repository in the CodeCommit console by choosing Clone URL.

![C9-clone](/images/mfe/C9-clone.png?classes=border,shadow)

When the cloning is complete, in the side navigation, expand the folder for your repository, and from the menu choose file, uplaod local files and upload the files provided by the instructor.

![Cloud9-import-file](/images/mfe/Cloud9-import-file.png?classes=border,shadow)

When you have finished importing files, in the terminal window, change directories to your cloned repository and then commit and push your changes. For example, if you added a new file named MyFile.py:

cd Shift-left-repo

 git status

 git add MyFile.py

 git commit -m "update"

 git push origin master

With the project enabled, click on the "configure" button:

![Click Configure](/images/mfe/clickconfigure.png?classes=border,shadow)

Scroll through the project's configuration, taking note of the enabled sections and what is configured there.  For instance you'll notice that the build is triggered automatically when AWS CodeCommit detects a change to code and sends a notification to the CodeCommitSQS queue.

  ![SQS Trigger](/images/mfe/sqstrigger.png?classes=border,shadow)

  Also note that the project is built from the latest source stored in AWS CodeCommit using Git (more on this later):

  ![Git AWS CodeCommit](/images/mfe/gitcodecommit.png?classes=border,shadow)

Click the "Enable Shift Left Inline Integration Box" (there is no need to change the other settings):

![Enable Shift Left](/images/mfe/enableshiftleft.png?classes=border,shadow)


### Repeat the above steps for the Medium and Hard projects!

#### You have successfully configured the Jenkins projects to work with MVISION Cloud!  Please move on to the next section to configure MVISION Cloud policies.

