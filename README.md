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

- Install AD on Virtual Machines (Domain Controller and Client-1)
- Create Admin and Normal User Account on AD
- Join Client to Domain Controller
- Setup Remote Desktop Access for non-admin users on Client-1

<h2>Deployment and Configuration Steps</h2>

<p>
  
![Screenshot 2024-03-07 184322](https://github.com/TiffanyChristman/configure-ad/assets/161388738/90b4fdcf-d5a3-43dd-8210-8836656e10fe)

</p>
<p>
Login to DC-1 and install Active Directory Domain Services, Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
Restart and then log back into DC-1 as user: mydomain.com\labuser
</p>
<br />

<p>
  
![Screenshot 2024-03-08 134358](https://github.com/TiffanyChristman/configure-ad/assets/161388738/14acd138-35b2-436e-92e8-29e97cf0a6dc)
</p>
<p>
In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”
Create a new OU named “_ADMINS”, Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”
Add jane_admin to the “Domain Admins” Security Group

</p>
<br />

<p>
  
![Screenshot 2024-03-08 134802](https://github.com/TiffanyChristman/configure-ad/assets/161388738/78bb4dab-600c-4e6a-b70b-b74d1345309a)

</p>
<p>
From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address, from the Azure Portal, restart Client-1
Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart),login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain

</p>
<br />

<p>
  
![Screenshot 2024-03-08 135405](https://github.com/TiffanyChristman/configure-ad/assets/161388738/f164a2c7-72cd-4848-a88b-79b9451ed119)
</p>
<p>
Log into Client-1 as mydomain.com\jane_admin and open system properties, click “Remote Desktop”
Allow “domain users” access to remote desktop, you can now log into Client-1 as a normal, non-administrative user now

</p>
<br />

<p>
  
![Screenshot 2024-03-08 135923](https://github.com/TiffanyChristman/configure-ad/assets/161388738/471bac87-dd57-4075-bb7e-5680e34ab84c)


</p>
<p>
Create a bunch of additional users and attempt to log into client-1 with one of the users, login to DC-1 as jane_admin
Open PowerShell_ise as an administrator, create a new File and paste the contents of the script into it
</p>
<br />

<p>
  
![Screenshot 2024-03-08 142433](https://github.com/TiffanyChristman/configure-ad/assets/161388738/805b4907-5083-463f-9136-f253e743e95b)

</p>
<p>
When finished, open ADUC and observe the accounts in the appropriate OU,attempt to log into Client-1 with one of the accounts (take note of the password in the script)


</p>
<br />

<p>
  


