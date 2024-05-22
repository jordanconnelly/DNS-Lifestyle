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
