<h1>Setting up Sentinel</h1>


<h2>Description</h2>
This project consists of how I set up Sentinel SIEM on my home environment. The goal of this lab is to simulate an enterprise grade infrustructure to have a base to simulate malicious attacks, which will be used to write reports and demonstrate other blue team activities in the future
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Bash (Linux)</b>

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
  
<h2>Step 3: Creating your Virtual Machine:</h2>

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
  Navigate to "Monitoring" and check the disabled option under Boot diagnostics :  <br/>
<img src="https://i.imgur.com/J1cxslZ.png" height="80%" width="80%" alt="Sentinel SIEM"/>
<br />
<br />
  Navigate to "Monitoring" and check the disabled option under Boot diagnostics :  <br/>
<img src="https://i.imgur.com/J1cxslZ.png" height="80%" width="80%" alt="Sentinel SIEM"/>
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
