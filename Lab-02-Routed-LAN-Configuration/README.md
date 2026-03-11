<h1>Lab #2: Building a Small LAN with a Router and Switch in Cisco Packet Tracer</h1>



<h2>Description</h2>
Design and implement a routed LAN in Cisco Packet Tracer by connecting three PCs to an access‑layer switch, uplinking the switch to a router, assigning IP addresses and default gateways, and verifying connectivity between hosts and the router with ping.
<br />


<h2>Utilities Used</h2>

- <b>Cisco Packet Tracer</b>
- <b>Command Prompt</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2></h2>
<h3>Step 1: Workspace Setup</h3>


Create a Basic Topology with a Switch, Router and 3 end hosts (PC0, PC1 and PC2) from the <strong>Devices Panel</strong>  <br/>

<strong>Devices Used:</strong><br/>
<ul>
  <li>Switch: 3560-24PS</li>
  <li>Router: 2901</li>
  <li>End Devices: PC </li>
</ul>
<p align="center">
<img src="https://i.imgur.com/lRv6b5q.png" height="80%" width="80%" alt="Workspace Setup"/>
<br />
<br />
 
<h3>Step 2: Cabling Connections</h3>

Using the <strong>Connections</strong> tab, cable all end devices to the access-layer switch, then connect the switch up to the router to complete the topology.

<strong>Ports Used:</strong><br/>
<ul>
  <li>PC Port: FastEthernet</li>
  <li>Switch Port: First available FastEthernet</li>
</ul>

After clicking a PC with the copper straight-through wire, select <strong>FastEthernet0</strong> when prompted, then repeat for the switch's first available FastEthernet port.<br/>

<p align="center">
<img src="https://i.imgur.com/EVPMOjT.png" height="80%" width="80%" alt="Cabling Connections"/>
<br/>
<br/>

The connections will show orange on the switch side initially and wait a moment for the ports to finish initializing before they turn green.</br>
<br/>

<p align="center">
<img src="https://i.imgur.com/ZMYzjr4.png" height="80%" width="80%" alt="Cabling Connections"/>
<br/>
<br/>

Using a copper straight-through cable, connect a GigabitEthernet port on the router to a GigabitEthernet port on the switch to establish the link.</br>
<br/>

<p align="center">
<img src="https://i.imgur.com/BPIbuEK.png" height="80%" width="80%" alt="Cabling Connections"/>


<br />
<br />

<h3>Step 3: Router Interface Configuration</h3>

After cabling, the connection between the router and switch will show as <strong>red</strong>, meaning the interface is administratively down. Click on the <strong>Router</strong>, open the <strong>CLI</strong> tab, and configure the interface to bring the link up and set it as the LAN's default gateway.<br/>


<strong>From the router CLI:</strong><br/>
<ul>
  <li>Enable the interface connected to the switch</li>
  <li>Assign the LAN IP address and subnet mask
    <ul>
    <li>IP Address: 192.168.21.1 | Subnet Mask: 255.255.255.0</li>
    </ul>
  </li>
  <li>Ensure the interface is up/up</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/MWRXN18.png" height="80%" width="80%" alt="IP Config"/>
 <br />

<br />
<br />

  
<h3>Step 4:PC IP Configuration</h3>

Configure each PC with its assigned IP settings. <br/>

<strong>IP Address Assigned:</strong><br/>
<ul>
  <li>PC 0: 192.168.21.11</li>
  <li>PC 1: 192.168.21.12</li>
  <li>PC 2: 192.168.21.13</li>
</ul>

<strong>Subnet Mask Assigned:</strong> 255.255.255.0<br/>
<strong>Default Gateway Assigned:</strong> 192.168.21.1<br/>

<p align="center">
<img src="https://i.imgur.com/3v68Uwb.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

<h3>Step 5: Ping Testing</h3>

Test end‑to‑end connectivity between PCs and to the router, using the <strong>Command Prompt</strong> within the Desktop Interface for each PC <br/>


<strong>Verification Steps:</strong><br/>
<ul>
  <li>From each PC, ping the router’s LAN IP: < strong>192.168.21.1</strong></li>
  <li>Ping between PCs</li>
  <li>Confirm all hosts receive successful replies</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/BlD1gfC.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

<h3>Conclusion and Key Takeaways</h3>

This lab successfully modeled a small Cisco LAN consisting of three PCs, an access‑layer switch, and a router providing Layer 3 IP connectivity. By designing an IP addressing plan, configuring the router’s LAN interface, and assigning correct IP settings and gateways on each PC, the network now supports reliable communication between all hosts and their default gateway. This environment serves as a practical foundation for future labs involving VLANs, inter‑VLAN routing, and more advanced switch and router features.

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

