<h2>Network File Shares and Permissions




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory environment installed
- A client machine running in Azure on a virtual machine (client-1 and joined to the domain

  


<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
  

<h2>High-Level Steps</h2>

- Step 1: Create resource group in Azure
- Step 2  Create two Windows 10 Virtual Machines, DC-1 and Client-1, these should already have had Active Directory installed
- Step 3: Inspect DNS A-Records on the server (hostname to IP addres mappings)
- Step 4:Create some of our own A-Records on the server and observe them from the client
- Step 5:Delete records from server and inspect/clear the client DNS cache to gain understanding
- Step 6:Touch on "CNAME" records (mapping one name to another name)
  

          
     

<h2>Actions and Observations</h2>

<p>   
</p>
<p>
<img src="https://i.imgur.com/5GZ2did.png" height="80%" width="80%" alt="Intall Windows Server Virtual Machine"/>
</p>
<p>
Create the Domain Controller VM (Windows Server 2022) named “DC-1”
Take note of the Resource Group and Virtual Network (Vnet) that get created at this time
</p>
<br />
<p>
<img src="https://i.imgur.com/pEatsVd.png" height="80%" width="80%" alt="Set Domain Controller NIC"/>
</p>
<p>Set Domain Controller’s NIC Private IP address to be static
</p>
<br />
<img src="https://i.imgur.com/XUhBNe0.png" height="80%" width="80%" alt="Set Domain Controller NIC"/>
<p>
<img src="https://i.imgur.com/w2DaBHa.png" height="80%" width="80%" alt="Diagram"/>
</p>
<p>
Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created in Step 1.a 
Ensure that both VMs are in the same Vnet 
</p>
<img src="https://i.imgur.com/MLMUc7X.png" height="80%" width="Attempt Ping Mainframe"/>
A-Record Exercise
</p>
Utilize Microsoft Remote Desktop to access Windows 10 virtual machine. Log into client-1 and attempt to ping mainframe using command prompt, "ping Mainframe"
</p>
</p>
<img src="https://i.imgur.com/PzaCrvm.png" height="80%" width="NS lookup mainframe"/>
</p>
Nslookup “mainframe” notice that it fails (no DNS record)
</p>
<img src="https://i.imgur.com/GfJr1u3.png" height="80%" width="Create DNS Record A"/>
</p>
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
</p>
<img src="https://i.imgur.com/EyYsLWT.png" height="80%" width="Ping mainframe"/>
</p>
Go back to Client-1 and try to ping it. Observe that it works
</p>
</p>
<img src="https://i.imgur.com/a36aLEt.png" height="80%" width="change address to 8.8.8.8"/>
</p>
Local DNS Cache Exercise
</p>  
<br />
Go back to DC-1 and change mainframe’s record address to 8.8.8.8
Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address

<img src="https://i.imgur.com/xbVwLRu.png" height="80%" width="Flush the DNS cache"/>
Observe the local dns cache (ipconfig /displaydns)  Flush the DNS cache (ipconfig /flushdns). Observe that the cache is empty
<img src="https://i.imgur.com/nHLpyvq.png" height="80%" width="Flush the DNS cache"/>
Attempt to ping “mainframe” again. Observe the address of the new record is showing up

<img src="https://i.imgur.com/7bRzFjJ.png" height="80%" width="create cname record"/>
CNAME Record Exercise

Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com”

<img src="https://i.imgur.com/6GTNX8O.png" height="80%" width="ping search google"/>
Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record

<img src="https://i.imgur.com/xZuLP59.png" height="80%" width="ping search google"/>
On Client-1, nslookup “search”, observe the results of the CNAME record
Finish
