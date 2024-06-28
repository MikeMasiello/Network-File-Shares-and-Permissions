<h2>Network File Shares and Permissions</h2>

In this walkthrough we will explore sharing resources out over the network, creating file shares to allow read, write, or deny access to individual users and groups. 


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory environment installed and running in Azure on a Virtual Machine (DC-1)
- A client machine running in Azure on a virtual machine (client-1 and joined to the domain)

  


<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
  

<h2>High-Level Steps</h2>

- Step 1: View diagram of file shares (what, when, where, why, and how)
- Step 2  Create and test some file shares
- Step 3: Talk about Security Groups (Windows and Active Directory)
- Step 4:Create and test some Security Groups
- Step 5:Clean up resources
  
  

          

<h2>Actions and Observations</h2>


<img src="https://i.imgur.com/0DyxPlr.png" height="50%" width="50%" alt="Create some sample file shares"/>  

Create some sample file shares with various permissions
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
Connect/log into Client-1 as a normal user (mydomain\<someuser>)
On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”
Set the following permissions (share the folder) for the “Domain Users” group:
Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
(Skip accounting for now)

<img src="https://i.imgur.com/eSKSb5D.png" height="50%" width="50%" alt="Access File Shares"/>  

Attempt to access file shares as a normal user
On Client-1, navigate to the shared folder (start, run, \\dc-1)
Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense?


<img src="https://i.imgur.com/dcKNRxp.png" height="50%" width="50%" alt="Create an “ACCOUNTANTS” Security Group"/> 
Create an “ACCOUNTANTS” Security Group, assign permissions, an test access
Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”

<img src="https://i.imgur.com/5lIlWwn.png" height="50%" width="50%" alt="Create an “ACCOUNTANTS” Security Group"/> 
On the “accounting” folder you created earlier, set the following permissions:
Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”

<img src="https://i.imgur.com/5ESORM0.png" height="50%" width="50%" alt="Create an “ACCOUNTANTS” Security Group"/> 
On Client-1, as  <someuser>, try to access the accountants folder. It should fail. 

<img src="https://i.imgur.com/Mjaeojl.png" height="50%" width="50%" alt="Add member to Accountants Security Group"/> 
Log out of Client-1 as  <someuser>
On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group

<img src="https://i.imgur.com/rz0xf6T.png" height="50%" width="50%" alt="Add member to Accountants Security Group"/> 

Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\ - Does it work now?  No! Must log off and back in to refresh it.

<img src="https://i.imgur.com/h3zLAvq.png" height="50%" width="50%" alt="Add member to Accountants Security Group"/> 

Restart Virtual Machines in Azure and via Remote Desktop to acess the accounting share. 

Finish
