<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Resources
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/mega8Ys.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/j9uTjkh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created in previous step:
</p>
<br />

<p>
<img src="https://i.imgur.com/F5PFNtW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set Domain Controller’s NIC Private IP address to be static:
</p>
<br />
<p>
<img src="https://i.imgur.com/cOnaVji.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Make sure both virtual machines are located within the same virtual network{Vnet}.
</p>
<p>you can verify the network topology using network watcher.</p>
<br />

<p>
 <img src="https://i.imgur.com/ot8Y8Yt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>Log into the VM and disable the Windows Firewall (for testing connectivity)</p>

<br />
<br />
<h3 
align="center;">Ensure Connectivity between the client and Domain Controller
</h3>
<br/>
<br />

<p> <img src="https://i.imgur.com/LlK8p45.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<br />
<br />
  <h3 align="center;">Install Active Directory</h3>
  <br />
  <br />
       
<p>Log in to DC-1 and install Active Directory Domain services. 
</p>
<p>
  <img src="https://i.imgur.com/HwI0W70.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Promote as a Domain Controller:</p>
<p><img src="https://i.imgur.com/Y45XBzL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<br />

<p>Setup a new forest as myactivedirectory.com</p> 
<p>(can be anything, just remember what it is - I ultimately did set it up as mydomain.com which you'll see in the next pic):</p>
<p> 
  <img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>
  
</p>
<br />
<p>Restart and then log back into DC-1 as user: mydomain.com\labusernet:</p>

<p><img src="https://i.imgur.com/Ou32bG9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<br />
<br />
<h3 align="center;">Create an Admin and Normal User Account in AD</h3>
<br />
<br />

<p>Using active Directory users and computers{ADUC}.</p>
<p>create two Organizational Unit{OUs} one named "_EMPLOYEES" and another named "_ADMINS".</p>
<p><img src="https://i.imgur.com/T07ajkH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p><img src="https://i.imgur.com/ksmisn0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>fef</p>

<br />

<P>create a new employee named"Jane Doe" with the username of "Jane_admin":</P>
<p><img src="https://i.imgur.com/JFY27me.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />

<p>add jane_admin to the "Domain Admins" Security Group</p>
<p><img src="https://i.imgur.com/ugAH3iR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />

<p>Sign out and close the RDP connection to DC-1.Then,log back in using the account</p>
<p>"mydomain.com\Jane_admin."use Jane_admin."From this point forward,use jane_admin as your administrator account.</p>
<p><img src="https://i.imgur.com/EZvfUt2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />
<p>Join Client-1 to your domain (mydomain.com)</p>
<br />
<br />
<h3 align="center;">Join Client-1 to your domain (mydomain.com)</h3>
<br />
<p>  From the Azure Portal,set Client-1's DNS settings to the DC's Private IP adress </p>
<p><img src="https://i.imgur.com/buO2SfO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />

<p>From the Azure Portal,restart Client-1</p>
<p>Login to Client-1 via RDP using the original local administrator account{labusernet}.</p>
<p>join the computer to the domain:note that this action will cause the computer to restart.</p>
<p><img src="https://i.imgur.com/rpJKk3X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<p>Log in to the Domain Controller using RDP and confirm Client-1 appears</p>
<p>in active directory users and computers {ADUC}within the "computers"container at the root of the domain.</p>
<br />

<p>Create a new OU named "_CLIENTS" and drag Client-1 into there:</p>
<p><img src="https://i.imgur.com/jrPRyce.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>


<br />
<h3 align="center;">Configure Remote Desktop access for non-administrative users on Client-1</h3>
<br />

<p>Log in to Client-1 using the account mydomain.com\jane_admin and open system properties</p>
<ul>
  <li>Navigate to the "Remote Desktop"section.</li>
  <li>Enable Remote Desktop access for"Domain users"</li>
</ul>
<p>This setup allows normal,non administrative users to log into Client-1.</p>
<p>Typically,this configuration is managed through Group Policy for efficient application across multiple systems.</p>

<p><img src="https://i.imgur.com/a8uYG8X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />
<br />
<h3 align="center;">Create a bunch of additional users and attempt to log into client-1 with one of the users</h3>
<br />

<ul>
<li>Login to DC-1 as jane_admin</li>
<li>Open Powershell_as an administrator.</li>
<li>Create a new file and paste the content script</li>
<li>https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1</li>
</ul>
<p><img src="https://i.imgur.com/3A0wAH1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />

<p>Execute the script and watch as the accounts are created.</p>
<p><img src="https://i.imgur.com/4oQqFBd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />

<p>Once completed,open Active Directory users and computera{ADUC}to verify that the accounts</p>
<p>are in the correct Organizational Unit{OU}.Then attempt to log into Client-1 using one of the newly</p>
<p>created accounts, making sure to reference the password specified in the script.</p>
<p><img src="https://i.imgur.com/yQcvCrT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p><img src="https://i.imgur.com/RIUedBR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p> I hope this tutorial helped you learn a little bit about network security protocols and observe traffic between virtual machines. This can be easily done on a PC or a Mac. Mac would just have an extra step to download the Remote Desktop App.</p>
<p>Now that we're done, DON'T FORGET TO CLEAN UP YOUR AZURE ENVIRONMENT so that you don't incur unnecessary charges.</p>
<p>Close your Remote Desktop connection, delete the Resource Group(s) created at the beginning of this tutorial, and verify Resource Group deletion.</p>


