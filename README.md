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

- Create a Resource Group
- Create a Virtual Machine
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>
<p align="center">
Set up your virtual environment
<p> Create your Resource group inside Azure
<p></p>
<img src="https://imgur.com/8UoHG5s.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

<p>

Create a Windows 10 Virtual Machine (VM)
<p> While creating the VM, select the previously created Resource Group
<p> While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
<p>
<img src="https://imgur.com/a6IpJQm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Create a Linux (Ubuntu) VM
<p> While creating the VM, select the previously created Resource Group and Vnet
<p>
<img src="https://imgur.com/78HbqrK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>

<p align="center">
Observe ICMP Traffic
<p> Use Remote Desktop to connect to your Windows 10 Virtual Machine
<p>
<img src="https://imgur.com/XlKRUg0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Within your Windows 10 Virtual Machine, Install Wireshark
<p>
<img src="https://imgur.com/XN8YHWH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
<p>Observe ping requests and replies within WireShark
<p>
<img src="https://imgur.com/2q18icI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/GMZNEYC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<p>
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
<p>
<img src="https://imgur.com/LzSzMNE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
<p> 
<img src="https://imgur.com/p8Il53N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
<p> 
<img src="https://imgur.com/16DPLva.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/zrqiQCq.png" width="80%" alt="Disk Sanitization Steps"/>
<p>
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
<p> Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
<p> Stop the ping activity
<p>
<img src="https://imgur.com/tglB0D4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>

<p align="center">
Observe SSH Traffic
</p>
Back in Wireshark, filter for SSH traffic only
<p> From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
<p> Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
<p> Exit the SSH connection by typing ‘exit’ and pressing [Enter]
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>

<p align="center">
Observe DCHP Traffic
<p>
<p> Back in Wireshark, filter for DHCP traffic only
<p> From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
<p> Observe the DHCP traffic appearing in WireShark
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>

<p align="center">
Observe DNS Traffic
<p>
<p> Back in Wireshark, filter for DNS traffic only
<p> From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
<p> Observe the DNS traffic being show in WireShark
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>

<p align="center">
Observe RDP Traffic 
<p>
<p> Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
<p> Observe the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
<p> Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>

Dont forget to clean up your Azure Environment to prevent incurring additional charges.
<p> Close your Remote Desktop connection
<p> Delete the Resource Group(s) created at the beginning of this lab
<p> Verify Resource Group Deletion

</p>
</p>

</p>
</p>

