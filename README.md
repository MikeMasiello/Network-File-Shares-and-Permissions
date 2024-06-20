<h2>Network File Shares and Permissions




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


<img src="https://i.imgur.com/0DyxPlr.png" height="80%" width="create cname record"/>  

Create some sample file shares with various permissions
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
Connect/log into Client-1 as a normal user (mydomain\<someuser>)
On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”
Set the following permissions (share the folder) for the “Domain Users” group:
Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
(Skip accounting for now)



Finish
