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

<p align="center">
Next we want to open up the Network Security Group(Firewall): <br/>
<img src="https://imgur.com/kGd9JCz.png" height="80%" width="80%""/>
 <p align="center"> We want to go into our Network Security group via Resource Groups in Azure. Then we want to go to the inbound 
                    rule section and remove the Remote Desktop Protocol inbound rule. We want to create our own inbound rule that 
                    will open our VM up to the public and make it attractive for attackers. So after we have removed this rule 
                    to the setting the allow for any kind of traffic to flow into the VM. This is what will create an attraction 
                    for other attackers. <br/>


<br />
<br /

<br />
<br />

<p align="center">
Now we want to Log into our VM: <br/>
<img src="https://imgur.com/Qj5cA0R.png" height="80%" width="80%""/>
 <p align="center"> Here we are looking to log into our VM and turn off the firewall so our attackers have the ability to invade 
                   the VM. So to log into the our VM we must go into Virtual Machines in Azure and click our VM. Then copy 
                   the public IP address in Azure.<br/>


<br/>
<br/>

<p align="center">
Remote Desktop: <br/>
<img src="https://imgur.com/SCphGLv.png" height="80%" width="80%""/>
 <p align="center"> After we have copied the public IP address, in the local computer access your Remote Destop Connection.
                    Put in the Username and ipaddress ass requested. After you have made your coonection you should see this 
                    certificate, click yes and you should have access to your Windows 10 VM.<br/>


<br />
<br />

<br />
<br/>

<p align="center">
Inside the VM <br/>
<img src="https://imgur.com/6u3ScAH.png" height="80%" width="80%""/>
 <p align="center">  When inside the VM go to the start button and open your firewall with. When it opens click Windows Defender
                     Firewall Properties and go through each tab Firewall State (Domain Profile, Private Profile, Public 
                     Profile and just turn them off. Hit Apply and OK<br/>


<br/>
<br/>
<p align="center">
Windows Firewall (example;) <br/>
<img src="https://imgur.com/YXP1tPZ.png" height="80%" width="80%""/>
 <br/>


<br />
<br />
<br/>
<br/>
<p align="center">
Windows Firewall Defender Properties Box (example;) <br/>
<img src="https://imgur.com/soID9YH.png" height="80%" width="80%""/>
 <br/>


<br />
<br />
<br />
<br/>

<p align="center">
 Pinging our VM <br/>
<img src="https://imgur.com/3ypJQ5A.png" height="80%" width="80%""/>
 <p align="center">  Now we want to ping our VM from our local computer to make sure that we reach out to the public internet, 
                     because if we can reach our VM from our local computer then everyone else can. So go to your command prompt
                     ,run as admin then ping and your VM ip address. If you get a reply that means you have the ability to reach 
                      your VM.<br/>


<br/>
<br/>
<br />
<br/>

<p align="center">
  We want to create a Log Repository <br/>
<img src="https://imgur.com/MOOrFbL.png" height="80%" width="80%""/>
 <p align="center">Next we are going to create a log repository for the VM to deposit their logs there. So the first thing 
                   we are going to do here is create a Log Analytic Workspace(this is going to be our log repository). 
                   So we go to Log Analytic Workspace and hit create. We will create a resource group (the resource group we 
                   created already), then we will name the analytic workspace and ensure that the workspace is in the same 
                   region as the VM and other components that we have created already. Then create and deploy.<br/>


<br/>
<br/>
<br />
<br/>

<p align="center">
  The next thing we want to do is create our Sentinel Instance <br/>
<img src="https://imgur.com/4fwdfQV.png" height="80%" width="80%""/>
 <p align="center"> A sentinel instance is a security information event management, it is a cybersecurity technology 
                    that monitors and analyzes security events across an IT environment. SIEM tools can help detect, 
                    investigate, and respond to security threats. So go to Microsoft Sentinel in Auzre and click create.
                    Then choose the Log Analytics workspace that we want to link to the Sentinel.Then add.This will link
                     our Log Analytics workspace to our sentinel instance so that we can get the logs in our repository from
                     the SEIM.<br/>


<br/>
<br/>
<br />
<br/>

<p align="center">
  The next thing we want to do is link our Virtual Machine to our Repository(Log Analytic Workspace) <br/>
<img src="https://imgur.com/ggGEFsW.png" height="80%" width="80%""/>
 <p align="center"> This means it creates a connection between Virtual Machine and Log Analytics Workspace so that we can 
                     receive logs in Sentinel and observe them. To do that we go to Microsoft Sentinel then we go to Content
                     Hub and click on Windows Security Events via AMA and install. After it is installs you must configure it.
                     So click open connector page. We need to create a data collection rule. This rule will be used for the 
                     VM to forward logs into our log analytics workspace.<br/>


<br/>
<br/>

<br />
<br/>

<p align="center">
  The Data Collection Rule <br/>
<img src="https://imgur.com/6oVVZBe.png" height="80%" width="80%""/>
 <p align="center"> When we have filled out this section this will install the Azure Monitor Window Agent within the VM. To 
                    verify go to VM then click extentions and applications.<br/>


<br/>
<br/>

<br />
<br/>

<p align="center">
  The Agent Monitor Windows Agent installed in the Virtual Machine <br/>
<img src="https://imgur.com/fmb5kAB.png" height="80%" width="80%""/>
 <p align="center"><br/>


<br/>
<br/>
<br />
<br/>

<p align="center">
  Now we need to deal with Logs in Log Analytics Workspace <br/>
<img src="https://imgur.com/bxLN1ZO.png" height="80%" width="80%""/>
 <p align="center"> So we are now going to Log Analytics Workspace, then look for Logs. Our VM should be sending logs here.
                    to see type security event and then run.<br/>


<br/>
<br/>
<p align="center">
  Security Event + Run (ie;) <br/>
<img src="https://imgur.com/DawKkSF.png" height="80%" width="80%""/>
 <p align="center"> You will see logs coming in from the VM. And the VM will be forwarding them using AMA. Security Event 
                    will usually dump out all the logs but if we want to review specific logs we will use the Query Language (KQL)
                    <br/>


<br/>
<br/>
<br/>
<br/>
<p align="center">
  Dealing with Geographical Data (ie; Global IP addresses) <br/>
<img src="https://imgur.com/tN6FFtz.png" height="80%" width="80%""/>
 <p align="center"> To figure out where all the logs are originating from we will need some sort of Geograpical Data. In order 
                    to do this we will import a spreadsheet for the logs that we will use to resolve IP addresses
                    to physical locations on a map. Microsoft Sentinal will make use of the spreadsheet of the global ip addresses
                    we have created. Go to Microsoft Sentinal in Azure.<br/>


<br/>
<br/>
<br/>
<br/>
<p align="center">
  Dealing with Geographical Data (Microsoft Sentinel) <br/>
<img src="https://imgur.com/QANNi6I.png" height="80%" width="80%""/>
 <p align="center">When in Microsoft Sentinel click on instance then go to watchlist and install the geo spreadsheet file. <br/>

<br/>
<br/>

<br/>
<br/>
<p align="center">
  Dealing with Geographical Data (Microsoft Watchlist-watchlist wizard) <br/>
<img src="https://imgur.com/QANNi6I.png" height="80%" width="80%""/>
 <p align="center">When in Microsoft Sentinel click on instance then go to watchlist and install the geo spreadsheet file. <br/>

<br/>
<br/>

<br/>
<br/>
<p align="center">
  Dealing with Geographical Data (Create a visual Map) <br/>
<img src="https://imgur.com/QANNi6I.png" height="80%" width="80%""/>
 <p align="center">The last thing we want to do is create a visual representation of the logs from users that are trying to access 
                   our VM. So in Sentinel go to workbooks. This is where will create the Map. Then add workbooks. Go to add Query.Then
                    advanced editor and paste the map (the map is a json representation of this item) into the query then click done 
                    editing. <br/>

<br/>
<br/>
<br/>
<br/>
<p align="center">
   The Geograhical Mapping of where our Attackers are coming from(Attack Map <br/>
<img src="https://imgur.com/tGqbeP7.png" height="80%" width="80%""/>
 <p align="center"> <br/>

<br/>
<br/>
