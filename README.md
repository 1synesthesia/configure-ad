<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Installation of Active Directory and Admin User Creation over the Cloud(Azure)</h1>
This tutorial outlines the installation and admin user creation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services


<h2>Operating Systems Used </h2>

- Windows Server 2025
- Windows 11 

<h2>High-Level Deployment and Configuration Steps</h2>

- [Step 1: Setup Domain Controller in Azure](#step-1:-create-resource-group-on-azure) 
- Step 2: Install Active Directory
- Step 3: Create a Domain Admin User

<h2>Deployment and Configuration Steps</h2>

<h3>Step 1: Create Resource Group on Azure</h3>
<br/>

<p>
<img width="724" height="331" alt="Screenshot 2026-07-08 234735" src="https://github.com/user-attachments/assets/3d3c18cf-c53b-4b87-b6d4-23c7d2124fef" />
</p>

<p>
- Open resource groups on Azure

- Click create in the top left

- Name your resource group and click create
</p>
<br/>

<h3>Step 2: Create your Domain Controller</h3>
<br/>

<p>
<img width="866" height="591" alt="createvm1" src="https://github.com/user-attachments/assets/f8f9d870-be0c-4226-832a-1d92ec356055" />
<img width="757" height="986" alt="createvm2" src="https://github.com/user-attachments/assets/98b5ee2e-ad85-4598-8a2c-b1e03077b2d7" />
<img width="752" height="694" alt="createvm3" src="https://github.com/user-attachments/assets/005dbf88-3c48-49aa-9213-87ff70eeecfb" />
</p>

<p>
- Open virtual machines

- Click create and then virtual machine

- Place your VM in the resource group you created previously

- Name your VM 'DomainController1'

- Choose 'Windows Server 2025 Azure Edition' as your image

- Create a username and password to use to connect to the Domain Controller through Remote Desktop

- Check the box verifying you have a license to use Windows

- (If you are using this tutorial to setup Active Directory configure your RDP port settings accordingly.)
</p>
<br/>

<h3>Step 3: Create a virtual network</h3>
<br/>

<p>
<img width="849" height="554" alt="createvirtualnet" src="https://github.com/user-attachments/assets/70ebcecb-b2e7-4691-958b-7c5c31e23b9f" />
</p>

<p>
- Create a virtual network that will be used as the virtual network for all company users

- Take note of the private IP address of the VM to be used to adjust DNS settings for all company users
</p>
<br/>

<h3>Step 4: Finish creating your Domain Controller</h3>
<br/>

<p>
<img width="756" height="1184" alt="createvm5" src="https://github.com/user-attachments/assets/16579869-6388-4920-aa1c-c9675229873c" />
</p>

<p>
- Click 'review and create' once you have succesfully setup your virtual network

- Verify all your settings are correct and click 'create'
</p>
<br/>



