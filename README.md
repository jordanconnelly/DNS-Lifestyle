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
<p>
<img src="https://imgur.com/v6Aij8W.png">


