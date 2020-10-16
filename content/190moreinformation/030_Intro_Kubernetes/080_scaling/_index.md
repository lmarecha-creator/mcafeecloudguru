---
title: "Connect MVISION Cloud to MS Azure"
chapter: false
weight: 300
---

MVISION Cloud utilizes MS Azure' comprehensive set of APIs to provide security for IaaS services such as Virtual Machine and Blob storage.  Later sections of this workshop will provide details on the details of the security provided, the following describes the functionality of MVISION Cloud for Azure at a high level:

![MVISION Cloud](/images/mfe/mvcforAWS.png?classes=border,shadow)


![MVISION Cloud](/images/mfe/MVC-azure2.png?classes=border,shadow)


In order to provide this security, your MVISION Cloud tenant will need access to various components of your Azure environment. 

### MVISION Cloud URL ###

https://www.myshn.net

1.  From the MVISION Cloud dashboard, click the configuration wheel and click **service management**.

  ![Enter Service Management](/images/mfe/MVC-Azure.png?classes=border,shadow)

2.  Click **Add Service Instance**, select Azure, and provide a name for the instance when promted ("Azure" will work just fine)

3.  On the **Account Settings** screen select the checkboxes shown below then click **next**.

  ![Enter Service Management](/images/mfe/MVC-features.png?classes=border,shadow)

4.  Acknowlege the pre-requisites and click **next**

5.  Click Provide API Credentials. Microsoft O365 (or Azure) login window appears.

6.  Enter your O365 (or Azure) credentials, or pick an existing account.

7.  Review the permissions and click Accept.

 ![MVISION Cloud for AWS Summary](/images/mfe/Azure-permission.png?classes=border,shadow)
 
8.  API Access is Enabled. Click Next.

9.  Select a Subscription ID from the list. Click Next.

 ![MVISION Cloud for AWS Summary](/images/mfe/Azure-sub-ID.png?classes=border,shadow)
 
10. Select the Subscription Owner's email to notify any Configuration Audit Policy violation incidents. Alternatively, you can manually enter an email in the description box.
 
11. Review your settings and click Save.

![MVISION Cloud for AWS Summary](/images/mfe/azure-summary.png?classes=border,shadow)

Azure is enabled in the Service Management page. 

Required Roles, in Azure users require the following Azure roles:

- Config Audit

. Reader
. Reader and Data Access

- Activity Monitoring

. Reader
. Reader and Data Access

- DLP and Malware (including Quarantine)

. Reader and Data Access

#### Configure Roles in Azure

1.  Log in to the Microsoft Azure Portal.

2.  Click Subscriptions.

![MVISION Cloud for AWS Summary](/images/mfe/Azure-roles.png?classes=border,shadow)

 Select the Subscription from the list. 


![MVISION Cloud for AWS Summary](/images/mfe/azure-role.png?classes=border,shadow)


 Go to Access control (IAM) > Check access > Add a role assignment. Click Add.


![MVISION Cloud for AWS Summary](/images/mfe/Azure-IAM.png?classes=border,shadow)


 Select a Role from the list. Select a user from the list, or search for a specific user. Click Save.


![MVISION Cloud for AWS Summary](/images/mfe/Azure-iam2.png?classes=border,shadow)


 Go to Role assignments and search for the user to verify the roles assigned.


![MVISION Cloud for AWS Summary](/images/mfe/Azure-iam3.png?classes=border,shadow)


#### Congratulations MVISION Cloud is now configured and ready for use with MS Azure!
