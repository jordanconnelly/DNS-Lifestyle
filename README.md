<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>DNS Records</h1>
In this tutorial, we will use the Active Directory (https://github.com/jordanconnelly/configure-ad) we created to observe DNS A-records and CNAME's. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Various Command-Line Tools

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- A-Record Creation and Observation
- DNS Cache Flush
- CNAME Record Creation and Observation

<h2>A-Record Exercise</h2>
</p>
<br />
First we will login to both DC-1 and Client-1 as the Domain Admin (jordan_admin). In Client-1 open the Command Prompt (Start>cmd>Enter). We will try to ping a computer named "mainframe", since it does not exist yet it will fail.
<p></p>
The Client-1 computer will search the DNS cache and Windows Host File for the computer "mainframe" first. When it does not find any computer by that name it will check the DNS Server, in this case DC-1, to see if there is any history of the computer "mainframe". Since there are no records of this in any of these three locations the ping fails.
<p>
<img src="https://imgur.com/v6Aij8W.png">
</p>
<br />
Now we will create an A-Reocrd for "mainframe". Open the DC-1 VM, then open the Server Manager. Click "Tools" in the top right and select "DNS" from the dropdown list. This opens the DNS Manager.
<p>
<img src="https://imgur.com/oyv4qYT.png">
</p>
<br />
From the menu on the left select DNS>DC-1>Forward Lookup Zones>mydomain.com
<p>
This shows the list of A-Records this computer currently knows.
<p>
<img src="https://imgur.com/Un9G8Wz.png">
</p>
<br />
To manually create a new A-record, right-click in the blank space and select "New Host". Type in the name (mainframe) and add an IP address. The IP address could be anything, but because we want to ping "mainframe" we will use DC-1's IP address(10.0.0.4). Click "Add Host". The mainframe A-record has now been successfully created.
<p>
<img src="https://imgur.com/tGtR3H4.png">
</p>
<br />
Go back to the Client-1 VM to ping "mainframe" again. Type "ping mainframe" in cmd again and hit Enter. Since there is now an A-record for "mainframe" we will see replies from the IP address we assigned to it(10.0.0.4).
<p>
<img src="https://imgur.com/lIHiaXZ.png">
</p>
<br />
We can also take a look at the local DNS Cache that the Client-1 VM currently knows, this is what we will be working with in the next exercise.
<p>
<img src="https://imgur.com/NkqoOME.png">
</p>
<br />
<h2>Local DNS Cache Exercise</h2>
</p>
We will go back to the DC-1 VM and change the "mainframe" record address to 8.8.8.8 within the DNS Manager. Select "mainframe" to open the Properties and change the IP address from 10.0.0.4 to 8.8.8.8, click Apply.
<p>
<img src="https://imgur.com/YknyDsU.png">
</p>
<br />
Minimize DC-1 and open Client-1. Open the Command Prompt again and type in "ping mainframe".
<p>
We will observe that the old IP Address (10.0.0.4) is presented, this is due to the Local DNS Cache. Since Client-1 has already interacted with "mainframe", the info associated with it is stored in the Local DNS Cache and does not reach out to the DNS Server for the answer. We can also type in (ipconfig /displaydns) to show the current DNS cache.
<p>
<img src="https://imgur.com/Ao16CQZ.png">
</p>
<br />
In order to get the updated IP Address for "mainframe" we will flush the DNS Cache. Open the Command Prompt as an Administrator and type in (ipconfig /flushdns). All the DNS records from Client-1 will be wiped, forcing it to ask the DNS Server (DC-1) for the answers. We can double-check this by typing (ipconfig /displaydns) and observing the DNS Cache is now empty. 
<p>
<img src="https://imgur.com/G9SwxoY.png">
</p>
<br />
Now we can type (ping mainframe) in Command Prompt again to observe the updated IP Address (8.8.8.8) that was received from the DNS Server (DC-1).
<p>
<img src="https://imgur.com/tP5tFs1.png">
</p>
<br />
