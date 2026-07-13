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

- [Step 1: Setup Domain Controller in Azure](#step-1-create-resource-group-on-azure) 
- [Step 2: Install Active Directory](#step-5-login-in-to-your-vm-through-remote-desktop)
- [Step 3: Create a Domain Admin User](#step-8-login-to-your-domain-controller-using-your-new-domain-name-through-remote-desktop)

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
</p>

<p>
- Open virtual machines

- Click create and then virtual machine
</p>
<p>
<img width="757" height="986" alt="createvm2" src="https://github.com/user-attachments/assets/98b5ee2e-ad85-4598-8a2c-b1e03077b2d7" />
</p>

<p>
- Place your VM in the resource group you previously created

- Choose your server location (dependent on your needs)

- Name your VM 'DomainController1' (or whatever is required for your needs)

- Choose 'Windows Server Azure Edition' as your image

- Choose a size for your VM (dependent on size of user base)
</p>

<p>
<img width="752" height="694" alt="createvm3" src="https://github.com/user-attachments/assets/005dbf88-3c48-49aa-9213-87ff70eeecfb" />
</p>
<p>
- Create a username and password to use to connect to the Domain Controller through Remote Desktop

- Check the box verifying you have a license to use Windows

- (If you are using this tutorial to setup Active Directory configure your RDP port settings accordingly)
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

<h3>Step 5: Login in to your VM through Remote Desktop</h3>
<br/>

<p><img width="2038" height="222" alt="createvm6" src="https://github.com/user-attachments/assets/b946df38-ac18-42fb-9763-dafe29f26d40" />
</p>

<p>
- Take note of your VMs public IP address in your virtual machines tab on Azure
</p>

<p><img width="403" height="481" alt="installad0" src="https://github.com/user-attachments/assets/7c136d9c-5b49-4a8d-ba4d-08b56fa5912f" />

</p>

<p>
- Access Remote Desktop on your computer

- Using your VMs public IP address and username/password that you setup; remotely connect to your Domain Controller
</p>
<br/>

<h3>Step 6: Install Active Directory</h3>
<br/>

<p><img width="229" height="27" alt="installad1" src="https://github.com/user-attachments/assets/72774891-d0b1-489a-8b78-e6f69dc705a1" />
</p>

<p>
- Once you are logged in the main page of the server will open

- Click on 'Add roles and features'
</p>

<p><img width="773" height="554" alt="installad2" src="https://github.com/user-attachments/assets/89b0de4a-0a49-4d95-9003-a9bc2a0e7e4e" />
</p>

<p>
- Choose your server as the destination
</p>

<p><img width="783" height="556" alt="installad3" src="https://github.com/user-attachments/assets/cf053780-ddb3-4379-bcd6-0a6281bd45f7" />
</p>

<p>
- Choose 'Active Directory Domain Services' as your role

- If you get a page asking you if you want to download auxillary features to help with AD allow it to install them as well
</p>

<p><img width="783" height="555" alt="installad4" src="https://github.com/user-attachments/assets/dee4ed0a-04d6-4217-9d68-fbcf4be4eaa9" />
</p>

<p>
- Once you have verified everything is correct on your confimartion screen click install
</p>

<p><img width="1900" height="1013" alt="installad5" src="https://github.com/user-attachments/assets/661441be-ca45-4236-9120-d9f3149ca0e7" />
</p>

<p>
- If you have done everything correctly your server should look something like this
</p>
<br/>

<h3>Step 7: Promote your server to Domain Controller</h3>
<br/>

<p><img width="1899" height="197" alt="promotedc1" src="https://github.com/user-attachments/assets/53fdce7b-f7b5-4c67-b004-be86f29f661d" />
</p>

<p>
- In the top right there will be flag with an active notification

- Open it and click 'Promote this server to domain controller'
</p>

<p><img width="755" height="552" alt="promotedc2" src="https://github.com/user-attachments/assets/4a68052d-b2fd-45e8-8d0b-40d14114da27" />
</p>

<p>
- On the first page click 'Add a new forest'

- Choose a domain name for your new forest
</p>

<p><img width="758" height="552" alt="promotedc3" src="https://github.com/user-attachments/assets/a49162ee-6e75-4822-8231-a08f91a566cd" />
</p>

<p>
- Create a password for restoration services in case of server failure in the future
</p>

<p><img width="759" height="556" alt="promotedc4" src="https://github.com/user-attachments/assets/2e719eb9-c676-49f8-88ea-adc1b9f7bf51" />
</p>

<p>
- You can leave everything else as is and continue to your prerequisite check

- If everything is correct you can click install

- Your server will restart after the installation is complete
</p>

<h3>Step 8: Login to your Domain Controller using your new domain name through Remote Desktop</h3>
<br/>

<p><img width="403" height="484" alt="adminusercreate1" src="https://github.com/user-attachments/assets/07f858ba-4eb7-4773-9d85-5b02fc5f8fa6" />
</p>

<p>
- Using your new domain name as a prefix (ex. www.mydomain.com\1syn) for your username to remotely connect to the server
</p>
<br/>

<h3>Step 9: Create an Admin User</h3>
<br/>

<p><img width="770" height="723" alt="adminusercreate2" src="https://github.com/user-attachments/assets/ed0b87a0-0fe6-4241-952f-af07ceaa9cda" />
</p>

<p>
- Access Active Directory Users and Computers
</p>

<p><img width="748" height="491" alt="adminusercreate3" src="https://github.com/user-attachments/assets/4683e2ca-f6b7-4b48-94bd-ad5cfc3ba2c3" />
</p>

<p>
- Right click on your domain name

- Under New click 'Organizational Unit'
</p>

<p><img width="431" height="354" alt="adminusercreate4" src="https://github.com/user-attachments/assets/a4fe8e06-e7ba-409b-a4d6-2e885eb658af" />
</p>

<p>
- Name your new OU something corresponding to admins
</p>

<p><img width="434" height="377" alt="adminusercreate5" src="https://github.com/user-attachments/assets/52031d5d-ffbb-4a72-909b-62783265025a" />
</p>

<p>
- Now right click on your new admin OU

- Under New click User

- Now create your admin profile
</p>

<p><img width="436" height="374" alt="adminusercreate6" src="https://github.com/user-attachments/assets/c8cde9b0-d124-4555-bec2-7cfd29371ba6" />
</p>

<p>
- Create a password for your admin profile

- Uncheck the box forcing a password change on next sign in
</p>

<p><img width="433" height="371" alt="adminusercreate7" src="https://github.com/user-attachments/assets/e0f88d88-edd9-4b66-83f5-b1cbafe084cd" />
</p>

<p>
- Create your new user
</p>

<p><img width="411" height="538" alt="adminusercreate8" src="https://github.com/user-attachments/assets/db5ab79f-1289-4213-bbe0-ef1106c3652f" />
</p>

<p>
- Right click on your new user in the admins OU

- Click on properties

- Go to 'Member of'

- Click Add
</p>

<p><img width="460" height="279" alt="adminusercreate9" src="https://github.com/user-attachments/assets/878e72ce-8377-456d-a991-33cb1fd3ffa5" />
</p>

<p>
- Type 'Domain Admins' in the object name box

- Click check names and an underlined 'Domain Admins' should be selectable

- Click Ok
</p>

<p><img width="408" height="536" alt="adminusercreate10" src="https://github.com/user-attachments/assets/a8d48696-f42f-42d0-b75f-068d3264c877" />
</p>

<p>
- If successful it should look like this
</p>

<p><img width="401" height="479" alt="adminusercreate11" src="https://github.com/user-attachments/assets/89899739-e469-4558-888b-af117b1e9ddc" />
</p>

<p>
- You should now be able to login as the new user you created

- This user is now your active Admin for the server
<p/>
<br/>

You Should now be ready to configure your Active Directory!
