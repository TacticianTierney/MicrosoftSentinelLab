<h1>Setting up Sentinel Honey Pot</h1>


<h2>Description</h2>
This project consists of how I set up Sentinel SIEM honeypot on my home environment to monitor security events. The goal of this lab is to simulate an enterprise grade infrustructure to have a base to simulate malicious attacks and be legitimately targeted by real malicious threats, which will be used to write reports and demonstrate other blue team activities in the future. 

DISCLAIMER!!!!
It is important to note that the configuration setting of this lab are INSECURE and not reccommended for an actual security environment, the SOLE purpose is to create an attack prone environment to demonstrate threats and create a threat map of attackers. I created the network and VM 24 hours prior with extremely poor security configuration and let it run overnight to capture the 4625 & other security logs.


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>KQL</b>

<h2>Environments Used </h2>

- <b>Windows 10 Pro (VM)</b> (22H2)
- <b>Windows 11 Home (Host)</b> (24H2)

<h2>Step 1: Creating your Resource Group:</h2>

<p align="center">
Make sure you have (or sign up for) a Microsoft Azure account and launch Azure in browser : <br/>
<img src="https://i.imgur.com/1XQwIZs.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Create Resource Group:  <br/>
Type in "Resource Group" in the search bar and navigate to "+ Create Resource Group"
<img src="https://i.imgur.com/4ZcbGgn.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Create a new Resource Group and enter a group name: <br/>
<img src="https://i.imgur.com/ZEu4twn.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
In the bottom left corner navigate to Review + Create:  <br/>
<img src="https://i.imgur.com/F7N6mTh.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Head back to "Resource Groups" and confirm your RG has been created:  <br/>
<img src="https://i.imgur.com/yk7Coqe.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />

<h2>Step 2: Creating your Virtual Network</h2>
<p align="center">
  Navigate to "Virtual Networks" and Create Virtual Network :  <br/>
<img src="https://i.imgur.com/vcpHnNx.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Name your Virtual Network, make sure its in the same resource group you created and the same region as the resource group:  <br/>
<img src="https://i.imgur.com/DhVmMoZ.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Click create, your settings should look like this:  <br/>
<img src="https://i.imgur.com/7Oiwhot.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Click create once again, wait until you see "Your deployment is complete" :  <br/>
<img src="https://i.imgur.com/pTms8zM.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  
<h2>Step 3: Creating your Virtual Machine (Honey Pot):</h2>

<p align="center">
Navigate to Virtual machines via the search bar or front page:  <br/>
<img src="https://i.imgur.com/nVDE8E5.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Create Virtual Machine:  <br/>
<img src="https://i.imgur.com/7RDBhXK.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Choose Azure Virtual Machine:  <br/>
<img src="https://i.imgur.com/0sbtyHg.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Navigate to Virtual machines via the search bar or front page:  <br/>
<img src="https://i.imgur.com/nVDE8E5.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Make sure your resource group is selected (it isnt by default), and name your virtual machine :  <br/>
<img src="https://i.imgur.com/IYXaigU.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Select Windows 10 as your OS under "Image *" :  <br/>
<img src="https://i.imgur.com/rjYZuPc.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Select a username and password, Check the box and click create:  <br/>
<img src="https://i.imgur.com/FkbrlLA.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Navigate to "Networking" in the tabs up the top of the review page and check this box :  <br/>
<img src="https://i.imgur.com/E1DKri3.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Navigate to "Monitoring" and check the disabled option under Boot diagnostics :  <br/>
<img src="https://i.imgur.com/J1cxslZ.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Go ahead and create your virtual machine:  <br/>
<img src="https://i.imgur.com/dwjrIVK.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Navigate to "Monitoring" and check the disabled option under Boot diagnostics :  <br/>
<img src="https://i.imgur.com/J1cxslZ.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />

<h2>Step 4: Alterning network rules:</h2>

<p align="center">
Go back to your resource group and navigate to the icon with the shield, your VM-nsg folder :  <br/>
<img src="https://i.imgur.com/3ZErf0l.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  For the purpose of this demonstration you want to delete this RDP protocol, as it allows anyone from any source to remotely access your network via RDP:  <br/>
<img src="https://i.imgur.com/rbjAUfN.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
Go ahead and add a new inbound rule, change the destination port ranges to *, which means ANY port destinations (Never actually do this indicated by the warnings at the bottom) :  <br/>
<img src="https://i.imgur.com/OFnaIfj.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  <h2>Step 5: Creating log repository and connecting to the SIEM:</h2>

<p align="center">
Navigate to Log Analytics Workspaces and create a new workspace, we are going to collect the logs from the VM we just created. :  <br/>
<img src="https://i.imgur.com/Rx1L4Wf.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Make sure you select your resource group and give your workspace a name :  <br/>
<img src="https://i.imgur.com/7A1eB9n.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Navigate to Microsoft Sentinel and create Micosoft Sentinel :  <br/>
<img src="https://i.imgur.com/5jReGk3.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Select your Workspace you just created and click create, you should see this page after about 60 seconds :  <br/>
<img src="https://i.imgur.com/0FmjyI3.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  To connect your logs from within the VM to our log workspace for sentinel to access go to content hub on the left bar :  <br/>
<img src="https://i.imgur.com/UPv20x5.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Search for security event and go ahead and install it :  <br/>
<img src="https://i.imgur.com/J2RnOAh.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Once installed, on the right side of the page click manage :  <br/>
<img src="https://i.imgur.com/Aol6eVi.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Select Windows security events via AMA :  <br/>
<img src="https://i.imgur.com/aQuS96N.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  On the right side of the page click open connector page :  <br/>
<img src="https://i.imgur.com/T2F7uhc.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Select Create data collection rule :  <br/>
<img src="https://i.imgur.com/rxn2kqN.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
   Make sure all your resources are selected and create the rule, leaving the rest of the options untouched :  <br/>
<img src="https://i.imgur.com/UAHT5Ph.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
   Head back to your Log workspace and click "Logs", run the query "SecurityEvents" in the KQL search box and it should look something like this, most of these security events will be malicious actors trying to access your virtual machine :  <br/>
<img src="https://i.imgur.com/VlivVDs.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
   The honeypot is now complete, Next lab will be creating an attack map in sentinel for these logs. Thanks for reading!:  <br/>
<img src="https://i.imgur.com/WorukSD.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
