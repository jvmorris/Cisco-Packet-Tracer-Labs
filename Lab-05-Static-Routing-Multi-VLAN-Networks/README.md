<h1>Lab #5: Static Routing Between Multi‑VLAN Networks in Cisco Packet Tracer</h1>



<h2>Description</h2>
Configure static routes between two multi‑VLAN networks in Cisco Packet Tracer by connecting routers over a serial link, assigning IPs to router interfaces and VLANs, enabling trunk ports, and using gateways of last resort to provide end‑to‑end connectivity between workstations.
<br />


<h2>Utilities Used</h2>

- <b>Cisco Packet Tracer</b>
- <b>Command Prompt</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2></h2>
<h3>Step 1: Workspace Topology Setup</h3>

Create the topology shown in the diagram:  <br/>

<strong>Devices Used:</strong><br/>
<ul>
  <li>Router: 2 x 2901</li>
  <li>Switch: 2 x 3560-24PS</li>
  <li>End Devices: 12 x PC</li>
  <li>Links: Ethernet links to switches, Serial link between routers</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/7gBkaT3.jpeg" height="80%" width="80%" alt="Workspace Setup"/>
<br />
<br />

<h3>Step 2: IP Addressing and VLAN Plan</h3>

Open the IP Configuration utility on each PC and assign VLAN-specific IP addresses and default gateways. <br/>

<strong>Router IP/VLAN Configuration Plan:</strong><br/>
<ul>
  <li>Router physical: 172.168.1.1 /24 on Gi0/1 </li>
  <li>VLAN 10 subnet: 192.168.10.1 /24</li>
  <li>VLAN 20 subnet: 192.168.20.1 /24</li>
  <li>VLAN 30 subnet: 192.168.30.1 /24</li>
</ul>

<strong>PC assignments:</strong><br/>
<ul>
  <li>VLAN 10:
    <ul>
      <li>PC1: 192.168.10.2 - Fa0/1</li>
      <li>PC2: 192.168.10.3 - Fa0/2</li>
    </ul>
  </li>
   <li>VLAN 20:
    <ul>
      <li>PC3: 192.168.20.3 - Fa0/3</li>
      <li>PC4: 192.168.20.4 - Fa0/4</li>
    </ul>
  </li>
  <li>VLAN 30:
    <ul>
      <li>PC5: 192.168.30.5 - Fa0/5</li>
      <li>PC6: 192.168.30.6 - Fa0/6</li>
    </ul>
  </li>
</ul>

<strong>Subnet Mask Assigned</strong>: <code> 255.255.255.240</code><br />
Each PC’s default gateway will be the matching router sub‑interface IP.<br>

<table align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/6SCuMtp.jpeg" height="250" width="300" alt="VLAN 10"/>
      <br><strong>VLAN 10</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/aQ7A4Al.jpeg" height="250" width="300" alt="VLAN 20"/>
      <br><strong>VLAN 20</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/aKxF5v7.jpeg" height="250" width="300" alt="VLAN 30"/>
      <br><strong>VLAN 30</strong>
    </td>
  </tr>
</table>
<p align="center">
PCs configured with VLAN-specific IPs and gateways, ready for connectivity testing.<br />

<p align="center">
<img src="https://i.imgur.com/JtEWhFt.jpeg" height="80%" width="80%" alt="IP Addressing and VLAN Plan"/>
<p align="center">
Complete IP/VLAN plan documented, ready for switch configuration.<br/>
<br />
 
<h3>Step 3: Cabling The LAN</h3>

Using <strong>Connections</strong> -> Copper Straight‑Through:<br>

<strong>Ports Used:</strong><br/>
<ul>
  <li>Switch: PCs on Fa0/1–Fa0/6</li>
  <li>Connect the switch uplink port (Fa0/24) to router Gi0/1</li>
</ul>

Wait until all links turn green to confirm a good physical connection.<br/>

<p align="center">
<img src="https://i.imgur.com/wQhrCtr.jpeg" height="60%" width="60%" alt="Cabling Connections"/>
<br/>
<br/>
