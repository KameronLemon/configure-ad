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

- Create a domain admin user and a client user within Microsoft Azure
- Join the client user to the admins domain
- Setup Remote Desktop for non adminstrative users on the client machine
- Create additional users and test login features with one of the users

![image](https://github.com/user-attachments/assets/36441046-625c-421b-907c-27cff29dc5d6)

</p>
<p>
Create two virtual (Admin center should run windows server 2022 datacenter and client machine should run regular windows 10) machines within microsoft azure that have two virtual cpus amd are within the the same network geographical region
</p>
<br />


![image](https://github.com/user-attachments/assets/47364a59-af52-4164-9660-52752e183ef3)

From the adminstrative machine disable the windows firewall to allow connectivity testing between the two machines.
</p>
<br />

![image](https://github.com/user-attachments/assets/7a69d268-9bb5-489e-bd64-63024078b427)

</p>
<p>
Back within azure join the client user to the admins domain by changing the client machines dns settings to the admins private ip address
</p>
<br />

![image](https://github.com/user-attachments/assets/b18f40cb-8904-4f2b-b796-52b8b1d2c584)

</p>
<p>
From the client machine within windows powershell ping the the administrative machines private ip address to ensure connectivity
</p>
<br />

![image](https://github.com/user-attachments/assets/f288bd53-3407-4985-b2e4-693715ab2808)

</p>
<p>Also within windows powershell run ipconfig /all to ensure the administrative machines private ip address is listed
</p>
<br />





