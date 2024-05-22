<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>DNS Records</h1>
In this tutorial, we create and observe (A) and CNAME records. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- A-Record Creation and Observation
- DNS Cache Flush
- CNAME Record Creation and Observation

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/chrisrraP/azure-network-protocols/blob/main/Ping%20Host%20From%20Client%20Fail.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/azure-network-protocols/blob/main/Create%20A-record.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/azure-network-protocols/blob/main/Ping%20to%20Host%20Success.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a virtual server and one client with Microsoft Azure. Reference https://github.com/chrisrraP/configure-ad to learn how to create virtual machines. Log into client and ping a record that has not yet been created. Using the domain server, create an A-record in the DNS Manager. Pinging the record name again from client VM will show it now exists in the DNS cache. 
</p>
<br />

<p>
<img src="https://github.com/chrisrraP/Record-Creation-and-Observation/blob/main/DNS%20Flush%20Results.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Using the domain server, change the host record's IP address. When pinging from the client machine, the old address will show. As an administrator, enter into command prompt (ipconfig/ flushdns). Ping again and the new address will show up in the refreshed cache.
</p>
<br />

<p>
<img src="https://github.com/chrisrraP/Record-Creation-and-Observation/blob/main/Cname%20Created.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/Record-Creation-and-Observation/blob/main/NSlookup%20Cname.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a CNAME record using the domain server that uses host name "search" to reach out to "www.google.com". Ping "search" from client VM and observe results. Utilize command prompt (nslookup search) to display additional address information. 
</p>
<br />
