---
title: "Create a Windows virtual machine"
date: 2018-10-03T10:21:11-07:00
draft: false
weight: 120
---

### Sign in to Azure 

Sign in to the Azure portal at https://portal.azure.com.

***Create virtual machine***

1- Type virtual machines in the search.

2- Under Services, select Virtual machines.

3- In the Virtual machines page, select Add.

4- In the Basics tab, under Project details, make sure the correct subscription is selected and then choose to Create new resource group. Type myResourceGroup for the name.

![ShiftLeft](/images/mfe/vm1.png?classes=border,shadow)


5- Under Instance details, type myVM for the Virtual machine name and choose East US for your Region, and then choose Windows Server 2019 Datacenter for the Image. Leave the other defaults.

![ShiftLeft](/images/mfe/vm2.png?classes=border,shadow)


6- Under Administrator account, provide a username, such as azureuser and a password. The password must be at least 12 characters long and meet the defined complexity requirements.

7- Under Inbound port rules, choose Allow selected ports and then select RDP (3389) and HTTP (80) from the drop-down.

![ShiftLeft](/images/mfe/vm3.png?classes=border,shadow)

8- Leave the remaining defaults and then select the Review + create button at the bottom of the page.

![ShiftLeft](/images/mfe/vm4.png?classes=border,shadow)

### Connect to virtual machine 

Create a remote desktop connection to the virtual machine. These directions tell you how to connect to your VM from a Windows computer. On a Mac, you need an RDP client such as this Remote Desktop Client from the Mac App Store.

1- Select the Connect button on the overview page for your virtual machine.

2- In the Connect to virtual machine page, keep the default options to connect by IP address, over port 3389, and click Download RDP file.

3- Open the downloaded RDP file and click Connect when prompted.

4- In the Windows Security window, select More choices and then Use a different account. Type the username as localhost\username, enter password you created for the virtual machine, and then click OK.

5- You may receive a certificate warning during the sign-in process. Click Yes or Continue to create the connection.

