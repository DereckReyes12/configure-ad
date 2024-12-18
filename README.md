<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

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
  <p> <img src="https://i.imgur.com/LlK8p45.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

  <br />
</p>
<br />
<p>installing active directory</p>
<p>
  <img src="https://i.imgur.com/HwI0W70.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
</p>
<br />
<p><img src="https://i.imgur.com/Y45XBzL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>
  
</p>
<br>
<p>
  <img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
</p>
<p>
  
</p>
<br />
<p><img src="https://i.imgur.com/Ou32bG9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>
  
</p>

<br />
<p>creating an admin and normal user account in AD</p>
<p><img src="https://i.imgur.com/T07ajkH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>ngenrengm
grgergr
gregreg
regr</p>
<br />
<p><img src="https://i.imgur.com/ksmisn0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>fef</p>
<br />
<p>
  <img src="https://i.imgur.com/JFY27me.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>r43r</p>
<br />
<p><img src="https://i.imgur.com/ugAH3iR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>dwefdwqedfwqe</p>
<br />

<p><img src="https://i.imgur.com/EZvfUt2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>regr</p>
<br />
<p>Join Client-1 to your domain (mydomain.com)</p>
<br />
<p><img src="https://i.imgur.com/buO2SfO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>
  
</p>
<br />
<p><img src="https://i.imgur.com/rpJKk3X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>efrtewfrewf</p>
<br />
<p><img src="https://i.imgur.com/jrPRyce.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p></p>

<br />
<p>Setup Remote Desktop for non-administrative users on Client-1</p>
<br />

<p>
 <img src="https://i.imgur.com/a8uYG8X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />
<p>Create a bunch of additional users and attempt to log into client-1 with one of the users</p>
<br />
<p>
  <img src="https://i.imgur.com/3A0wAH1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />
<p><img src="https://i.imgur.com/4oQqFBd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p></p>
<br />
<p><img src="https://i.imgur.com/yQcvCrT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p></p>
<br />
<p><img src="https://i.imgur.com/RIUedBR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

