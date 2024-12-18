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

1. Create another VM and name it VM-2
2. While creating VM2, select the previously created Resource Group and Vnet
3. Create a Linux (Ubuntu)
4. Make the same username and password as VM-1.

<p>
<img src="https://i.imgur.com/cNyYDVu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/cNyYDVu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

5. In the network tab choose the same Virtual Network as VM-1( if you don't see VM-1 network check to see if VM-1 is done being created).

<p>
<img src="https://i.imgur.com/sL7tJAo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

6. Click Review + Create!
   
<h2>Observe ICMP Traffic</h2>

1. Log into VM-1 using a remote desktop
2. Download and Install Wirweshark
3. Enter the Ethernet Tab to begin capturing network traffic!

<p>
<img src="https://i.imgur.com/f1WWcCX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/OpUCJfJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

4. Filter for ICMP(Internet Control Message Protocol) traffic.
5. ICMP determines whether or not data is reaching its intended destination.
6. Open up Windows PowerShell and ping VM-2 private IP address.
7. You can find VM-2 private IP address in the Azure Portal under networking.

<p>
<img src="https://i.imgur.com/PB1G7KS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

8. You can observe the ping request in WireShark.
9. Source: 10.0.0.4 (VM-1 private IP address).
10. Destination: 10.0.0.5 (VM-2).
11. Protocol: ICMP
12. Request followed by the reply from VM-2.

<p>
<img src="https://i.imgur.com/Yy7dpf9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

13. You can also observe the traffic from a website.
14. From The Windows 10 VM, open the command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in Wireshark
15. The destination IP address (172.217.12.142) is Google's public IP address.

<p>
<img src="https://i.imgur.com/SbJ9Y00.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/oGODae6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

16. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM.
17. The command for perpetual ping is -t (ping 10.0.0.5 -t).

<p>
<img src="https://i.imgur.com/xgfyRMf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/F0ETedo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h2>ICMP + Firewalls</h2>

- To get a basic idea of how firewalls work we will block IMCP traffic from VM-2 firewall and observe the results.
- Go back to the Azure portal go to Network Security groups and click on VM-2.
