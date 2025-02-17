# SOCLabintheCloudusingAzure

 ### [Pictoral Walkthrough Demonstration]

 <h2>Description</h2>
 In this lab we are going to create a basic home SOC in the Cloud using Azure. So the plan is to sign onto Azure creating a free subscription. Then we are going to create a HoneyPot in Azure, which will bascially be a virtual machine, then we are going to open up that virtual machine to the public to be attacked intentionally.We are going to configure log forwarding to forward the log in failed attack attempts to a central repository. Then we are going to connect that central repository to a SEIM (Azure Sentinel). Lastly, we are going to create an attack map that should show where all the attackers are coming from.

<h2>Languages and Utilities Used</h2>

- <b>Azure and its Features</b> 
- <b>Virtual Machines</b>
- <b>Azure Sentinel</b>
- <b>etc</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>
<p align="center">
Creating our Azure account: <br/>
<img src="https://imgur.com/cg8MANR.png" height="80%" width="80%" "/>
<p align="center"> We will start this Lab by creating our Azure account. Here you can create 
                   a free account using a credit card. <br/>
 
<br />

<p align="center">
Next we want to Create a Resource Group: <br/>
<img src="https://imgur.com/2YUZbJw.png" height="80%" width="80%""/>
 <p align="center"> After you have created your Azure account and log in you need to first create a Resource Group. A resource group is like a folder for cloud resources like Virtual Machines, Virtual Networks etc. After we have created our research group we want to create a Virtual Network inside of the resource group. Then we will create a virtual machine and attach it to the virtual network. We will log into the virtual Machine, turn off the Firewall, to make it enticing to attackers. We will also make a network security group, thisi is like a cloud firewall which we will also completely open it up as well to attackers.  So we hit the setting create, then give the resource group a name ie;RG-SOC-Lab, then put it in a region: ie;East US 2-This mean the when we create the folder in the cloud it will exists in a Azure Datacenter somewhere on the Eastern part the United States, then create the group folder.
                  <br/>


<br />
<br />

<br />

<p align="center">
Next create the Virtual Network: <br/>
<img src="https://imgur.com/2EUJzlo.png" height="80%" width="80%""/>
 <p align="center"> After you have created a Resource Group, go to Virtual Network. A virtual network is like your home router 
                    that your computer plugs into that connect to the WI-FI, but in the cloud. So hit create, name your virtual 
                    network ie; "vnet-soc-lab", you can leave the other settings defaults but ensure that the virtual network is 
                    in the smae region as your resouce group<br/>


<br />
<br />

<p align="center">
Note: If you go back to the resource group you should see our virtual network we created  <br/>
<img src="https://imgur.com/UYyStYt.png" height="80%" width="80%""/>



<br />
<br />

<br />

<p align="center">
Next create the Virtual Machine: <br/>
<img src="https://imgur.com/8Qq5XTT.png" height="80%" width="80%""/>
 <p align="center"> After you have created your Virtual Network, the next step is to crete a VM. This will be our HoneyPot exposed 
                    to the internet that the public will attack. So hit create, then next resource groups-choose the name of the 
                    resource group you created already,give you VM a name (ie;CORP-NET-EAST1), give it a username and password.
                    Create and Deploy the VM, Note: again if you go back to your resource group, then click your Virtual Network, 
                    within the Virtual Network you should see your virtual machine, and other components like your public ip
                    address, a network security group, and a network interface.<br/>


<br />
<br />

