<h1>Lab #2: Building a Small LAN with a Router and Switch in Cisco Packet Tracer</h1>



<h2>Description</h2>
Design and implement a simple Layer 2 Ethernet LAN in Cisco Packet Tracer by connecting two PCs to a switch, assigning appropriate IP addresses, and verifying end-to-end connectivity using ping.
<br />


<h2>Utilities Used</h2>

- <b>Cisco Packet Tracer</b>
- <b>Command Prompt</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2></h2>
<h3>Step 1: Workspace Setup</h3>


Create a Basic Topology with a single Switch and 2 end hosts (PC1 and PC2) from the <strong>Devices Panel</strong>  <br/>

<strong>Devices Used:</strong><br/>
<ul>
  <li>Switch: 2960</li>
  <li>End Devices: PC </li>
</ul
<p align="center">
<img src="https://i.imgur.com/dpZI70X.png" height="80%" width="80%" alt="Workspace Setup"/>
<br />
<br />
 
<h3>Step 2: Cabling Connections</h3>

Connect each PC to the switch by navigating to <strong>Connections</strong> and using copper straight‑through cables, then wait until all links turn green to confirm a good connection.<br/>

<strong>Ports Used:</strong><br/>
<ul>
  <li>PC Port: FastEthernet</li>
  <li>Switch Port: First available FastEthernet</li>
</ul>
<p align="center">
<img src="https://i.imgur.com/LxyTAtZ.png" height="80%" width="80%" alt="Cabling Connections"/>
<br />
<br />

<h3>Step 3: IP Config</h3>

Assign IP Addresses to both PCs using the IP Configuration within the Desktop Interface for each end device <br/>

<strong>IP Address Assigned:</strong><br/>
<ul>
  <li>PC 1: 192.168.0.1</li>
  <li>PC 2: 192.168.0.2</li>
</ul>

<strong>Subnet Mask Assigned:</strong> 255.0.0.0<br/>
<p align="center">
<img src="https://i.imgur.com/rf0MFLF.png" height="80%" width="80%" alt="IP Config"/>
 <br />

<div style="display: flex; justify-content: center; gap: 20px;">

  <img src="https://i.imgur.com/NS5gA1w.jpeg" height="45%" width="45%" alt="PC1 IP Configuration"/>

  <img src="https://i.imgur.com/L9OYMUF.jpeg" height="45%" width="45%" alt="PC2 IP Configuration"/>

</div>

<br />
<br />
<br />
<br />
 
<h3>Step 4: Ping Testing</h3>

Use one PC to ping the other's IP Address using the Command Prompt within the Desktop Interface for each PC <br/>
<p align="center">
<img src="https://i.imgur.com/9SqRRgS.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

<h3>Conclusion and Key Takeaways</h3>

This lab successfully built a basic Ethernet LAN in Cisco Packet Tracer by connecting two PCs to a switch, assigning IP addresses, and validating connectivity with ICMP ping. By setting up the physical topology, configuring the correct cabling, and applying consistent IP settings on both hosts, the environment now demonstrates fundamental Layer 2 and Layer 3 communication. This provides a solid foundation for future labs involving VLANs, inter‑VLAN routing, and more advanced switch and router configurations.

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

