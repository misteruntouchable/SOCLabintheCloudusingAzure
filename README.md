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
 <p align="center"> We want to download our Windows Server 2019 ISO and Windows 10 ISO.
                    Then we want to set up our server within our Virtual Box. Give it a name.(ie; DC)
                    Set other parameters for your VM like RAM,Number of Processors,Network Adapters(NAT,
                    Internal Network),Storage. Remember to put the ISO server in the Optical Drive  
                  <br/>


<br />
<br />
