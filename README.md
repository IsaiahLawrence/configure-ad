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
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1- We need to set up our server on azure. I'm going to use a VM that's running Windows server 2022 We'll also create a VM that's using windows 10 and that computer will connect to our server
- Step 2- In azure the server we created; set it's ip configuration to static (this just means the ip address doesn't change)
- Step 3- Once both machines are set up we ping the server; if request times out we open up the firewall on our server to allow pings as pictured below we enabled ICMPv4 echo request which allowed us to ping our server
-   ![image](https://github.com/IsaiahLawrence/configure-ad/assets/152194351/a20d6bd0-503d-4885-91f7-ad41aa4d0102)

- Step 4- We need to install Active Directory Domain Services through the server manager.  ![image](https://github.com/IsaiahLawrence/configure-ad/assets/152194351/542f3b10-d2cf-4068-b442-c4f2f74b00fc)

- Step 5- Once we finish that step we'll click the flag in the top right corner and promote this server to domain controller, select add a new forest and enter our domain name (it can be anything) I chose ExampleDomain.com ![image](https://github.com/IsaiahLawrence/configure-ad/assets/152194351/36c9175b-e10a-475a-a55c-072d38d6e883)

- Step 6- Once installed we can go to tools on the server manger dashboard then Active Directory users and computers, here we can create new "folders" or organizational units. We'll create 2 one for employees and one for admins seen at the bottom of the list here. ![image](https://github.com/IsaiahLawrence/configure-ad/assets/152194351/4f48ab47-6cb7-42bf-80c8-4433caf59839)

- Step 7- We'll create a new employee and admin; To give admin permissions to a user you must add them to the domain admins group like so  ![image](https://github.com/IsaiahLawrence/configure-ad/assets/152194351/6c58dd9d-e147-4748-a134-02a3d21f10b3)

- Step 8- Now since we've set up our server and made it's IP static we can get on our other VM our windows10 machine and connect to it. 1st we'll go to azure and change our DNS server to our servers private IP, then we will reset our machine and log back in. Once logged back in we can go to system settings and rename PC(advanced) enter the domain we used in this case it's exampledomain.com after that's complete we'll be asked to log in with an account that has permission. This will be the admin account we created on our server.  ![image](https://github.com/IsaiahLawrence/configure-ad/assets/152194351/a5d62eaa-57bc-4ad6-a692-5c7cf20e295c)

- After signing on you'll have a pop up window that says "welcome to the exampledomain.com domain." The computer will need to restart. When the computer reboots we will be able to log in to the admin account on our windows 10 device, because they share the same domain now.

- From our windows 10 machine we'll log in as admin and allow remote desktop for all domain users, this is so after we create users we'll be able to log into this computer. We can find the settings to allow this in remote desktop then clicking "select users that can remotely access this PC". We'll then add domain users.

  
![image](https://github.com/IsaiahLawrence/configure-ad/assets/152194351/6b36c47e-955b-48d5-8b4c-5a7e5bc7ff0d)





<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

