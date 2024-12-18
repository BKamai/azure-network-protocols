<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

1. Create Resources in Azure
2. Observe ICMP Traffic
3. Observe SSH Traffic
4. Observe DHCP Traffic
5. Observe DNS Traffic

<h2>Actions and Observations</h2>

1. Create a Windows 10 Virtual Machine in Azure.

<p>
<img src="https://i.imgur.com/WPH1Ure.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/EAgrGj4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

2. Create a new resource group.
3. Name this Virtual Machine VM-1.
4. For the image choose Windows 10 Pro, version 22H2 - x64 Gen2 (free services eligible).

<p>
<img src="https://i.imgur.com/FGLwxmc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

5. Create a username and password(don't forget your username and password!).

<p>
<img src="https://i.imgur.com/4RwvtcM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

6. Wait for the validation process and hit create.

<p>
<img src="https://i.imgur.com/dH90bXC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

6. Ensure this VM creates a new virtual network is made, we'll be connecting our Linux VM shortly.

<p>
<img src="https://i.imgur.com/zdWOsr4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

9. Click Review + Create!

<h2>Create a Linux Virtual Machine</h2>
