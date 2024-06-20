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

<p>   

</p>
<br />

</p>
<br />


</p>
Utilize Microsoft Remote Desktop to access Windows 10 virtual machine. Log into client-1 and attempt to ping mainframe using command prompt, "ping Mainframe"





<img src="https://i.imgur.com/7bRzFjJ.png" height="80%" width="create cname record"/>
CNAME Record Exercise

Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com”

<img src="https://i.imgur.com/6GTNX8O.png" height="80%" width="ping search google"/>
Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record

<img src="https://i.imgur.com/xZuLP59.png" height="80%" width="ping search google"/>
On Client-1, nslookup “search”, observe the results of the CNAME record
Finish
