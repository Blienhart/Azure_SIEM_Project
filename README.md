 Azure_SIEM_Project
 <h2>Description</h2>
 in this walkthrough, we will setup a Azure Si Sentinel (SIEM) on a public facing virtual machine for the purpose of monitoring and understanding the fundamentals in a SoC analyst role.
 <br/>

<h2>Preface</h2>

The skills you will learn in this walkthrough is how to architect a cloud Virtaul Machine using Azure Sentinel as an acting network monitor, and configuring the SIEM to acts as a "Honey Pot".
Before we start go ahead and create an account with Microsoft Azure the link is https://azure.microsoft.com/en-us/free/ , select the free plan. If for some reason after you cannot find the dashboard the URL is portal.azure.com/home <br />

<p align="center">

<h2>Lets Begin</h2>


  Once you get to your dashboard, click the search bar at the top and type in Virtual Machines. then select create new Azure Virtual Machine. Should look something like this: 
  <br/>


  
<img src="https://i.imgur.com/cuKQsnF.png" height="80%" width="80%" alt="AzureSIEMProject"/>
<br />

<h2>Configuring your virtual box</h2>

Next, at the top under subscription create a new Resource group lets call it HoneyPotLab. feel free to name the virtual machine below whatever you like. This will come handy later 
when we set up the network to keeps all the resources in one project.
For region select US WEST 3,
then no infrastructure required,
select standard for security and for your image choose windows 10 pro 22h2 x64 gen 1. I believe gen 2 costs money so for the sake of this free lab choose one.
Size will be Standard_b1s -1 vcpu 1gb mem.
then select a username and password for the admin account (just make sure you remember it). 
After that just check the box by licensing to confirm hosting rights and then click next to go the disks config.
If you got lost somewhere in that refer to the screenshot below ---VVV

<br/> 

<img src="https://i.imgur.com/zDeoytP.png" height="80%" width="80%" alt="AzureSIEMProject"/>
<br/>

<h2>Skip disks and move onto Networking</h2>

for disks we will leave this alone go ahead and click next again to go to the Networking config. 
First select NIC security group and click advanced; then next to configure network security group click create new underneath the drop down menu. 
Think of this as a firewall essentially, and we need to configure it to be open to the public so we can monitor for bad actors. 
<br/>

change source to any, 
but an astrich for source port ranges and destination port ranges to allow for all.
I want to emphasize that this is just a lab and no real data is at risk here, as a SoC architect you should never make such a rule when building your employers SIEM.
set priority to 100 and give it whatever name you like. screenshot below for reference.

<br/> 

<img src="https://i.imgur.com/LkbeTry.png" height="80%" width="80%" alt="AzureSIEMProject"/>
<br/>

Add the rule the click okay. 

<br/> 

<img src="https://i.imgur.com/ZdkPWns.png" height="80%" width="80%" alt="AzureSIEMProject"/>
<br/>

then click review and create, after that click create in the bottom left hand corner like in the image below. it may take a few minutes to spin up the machine.


<br/>

<img src="https://i.imgur.com/DuLaPeD.png" height="80%" width="80%" alt="AzureSIEMProject"/>
<br/>






