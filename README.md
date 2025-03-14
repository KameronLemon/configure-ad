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

![installactdomantoserver](https://github.com/user-attachments/assets/238994aa-16e2-4b20-950a-ebabd920c776)
![Capture](https://github.com/user-attachments/assets/5c45e0b7-0180-48c0-b923-8f858a90e477)
![3](https://github.com/user-attachments/assets/fbc642c5-c965-410f-998d-a9b60b1c3ed2)

</p>
<p>From the server manager application within the administrative machine install active directory domain services and allow all needed features to be installed
</p>
<br />

![promo to domain controller](https://github.com/user-attachments/assets/86a3d950-47d0-4fcc-b931-ee8dc9cb46fc)

</p>
<p>After installation completion promote server to a domain controller
</p>
<br />

![addnewforest](https://github.com/user-attachments/assets/75a592db-0e8a-47eb-86ca-f8f2d71887b1)
![Capture](https://github.com/user-attachments/assets/2dc8ce31-9277-465c-8f70-df3530717f2c)
![Cap2ture](https://github.com/user-attachments/assets/5ab33e1f-533c-49e9-8b21-59188f53ded8)

</p>
<p>After prompting to promote your server to a domain controller setup a new forest (for this lab it will be labled as mydomain.com) your computer will restart and you need to login with the credentials you created
</p>
<br />

![Capture](https://github.com/user-attachments/assets/252d1c87-b1f8-475a-853d-ecf4d46a31aa)
![Captur2e](https://github.com/user-attachments/assets/3ae6399d-b52d-45ce-915f-bbb4ad3f08b5)

![Capture3](https://github.com/user-attachments/assets/cd2d6a50-8748-4685-aa62-f308674b4c73)

</p>
<p>Within active directory users and computers, create two orginizational unites. One labled "_EMPLOYEES" and one called "_ADMINS"
</p>
<br />

![Capture12](https://github.com/user-attachments/assets/599372fa-e515-4df4-aee9-5a3f7f02f959)

![Capture](https://github.com/user-attachments/assets/8eee6619-2464-4be1-926d-c2ff13916db1)

![Capture4](https://github.com/user-attachments/assets/a4e99a1c-66bb-4ea2-8bcd-c954c6a58f2d)

![Capture6](https://github.com/user-attachments/assets/83921f47-9c4e-4cb4-8de4-97a2798e43cf)

</p>
<p>Create a brand new employee named “Jane Doe” (same password) with the username of “jane_admin” / Cyberlab123!". Then Add jane_admin to the “Domain Admins” Security Group. 
  After that disconnect from your administrative machine and log back in as “mydomain.com\jane_admin”. (Use the user jane_admin as your admin account from now on)
</p>
<br />

![Captur2e](https://github.com/user-attachments/assets/918e8212-d267-48d9-a7c0-fa8b0c079466)

![Capture3](https://github.com/user-attachments/assets/02fad1ca-6d6a-4f6d-a376-4ad0b90ea784)

![Captur7e](https://github.com/user-attachments/assets/0729d15b-7e63-438e-8596-8657c929c2ee)

login into your client machine as your local admin. Then join it to your domain controllor from your sytem properties.

![Capture5](https://github.com/user-attachments/assets/d4430091-5c47-4c01-ba7f-ed2dd50dfcee)

Verify client machine appears in active directory users and computers.

![Capture2](https://github.com/user-attachments/assets/6ea1e30c-1a8f-488f-adca-b4a0a905fc7f)
![Capture3](https://github.com/user-attachments/assets/a88b4991-ef22-4367-bd57-da3b45e71143)

login to the client machine as Jane_admin and allow domain users to access remote desktop.

![Capturescript](https://github.com/user-attachments/assets/97accfba-9512-462d-a237-5983aa2aaa03)
![Capture4](https://github.com/user-attachments/assets/3807131e-380b-4e98-b231-a117e0fa7027)
![Captudjre](https://github.com/user-attachments/assets/66623cab-a16f-41b0-9733-ff563c0e90d6)
![Captureredux](https://github.com/user-attachments/assets/191fad95-017b-4395-b7bc-d181d22e877c)

Create new users within "_EMPLOYEES". (I'm utilizing a script within windows powershell that creates 10,000 new users however this is not neccesary) just create a few new ones within active directory and computers. Check the "_EMPLOYESS" orginizational unit to ensure users are created. Select a random user and attempt login with the user credentials. 

![log it](https://github.com/user-attachments/assets/478b2dfe-562b-4773-9841-54929991e102)

Congratulations you've succesfully deployed Active Directory within Azure Virtual Machines! If you need any help feel free to connect and reach out to me via LinkedIn.


































