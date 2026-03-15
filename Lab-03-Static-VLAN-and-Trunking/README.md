<h1>Lab #3: Basic VLANs and Trunking in Cisco Packet Tracer</h1>



<h2>Description</h2>
Configure static VLANs and an 802.1Q trunk in Cisco Packet Tracer by segmenting two switches into multiple VLANs, assigning access ports for eight PCs in a single subnet, and verifying end‑to‑end connectivity across the trunk.
<br />


<h2>Utilities Used</h2>

- <b>Cisco Packet Tracer</b>
- <b>Command Prompt</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2></h2>
<h3>Step 1: Workspace Setup</h3>


Create a Physical Topology with 2 Switches and 8 PCs from the <strong>Devices Panel</strong>, with 4 PCs connected to each switch and a single uplink link between the two switches.  <br/>

<strong>Devices Used:</strong><br/>
<ul>
  <li>Switch: 2 x 3560-24PS</li>
  <li>End Devices: 8 x PC </li>
</ul>

<p align="center">
<img src="https://i.imgur.com/lRv6b5q.png" height="80%" width="80%" alt="Workspace Setup"/>
<br />
<br />
 
<h3>Step 2: Cabling The Access Layer</h3>

Using the <strong>Connections</strong> tab, connect each PC to its local switch using copper straight‑through cables.

<strong>Ports Used:</strong><br/>
<ul>
  <li>Switch1: PCs on Fa0/1–Fa0/4</li>
  <li>Switch2: PCs on Fa0/1–Fa0/4</li>
</ul>

Wait until all PC-Switch links turn green to confirm a good physical connection.<br/>

<p align="center">
<img src="https://i.imgur.com/EVPMOjT.png" height="80%" width="80%" alt="Cabling Connections"/>
<br/>
<br/>


<h3>Step 3: Configuring VLANs on Both Switches</h3>

Open the CLI for each switch and configure the VLANs and access ports.<br/>

<strong>VLAN Configuration:</strong><br/>
<ul>
  <li>Create VLAN 10 `code here`
  <li>VLAN 10 – VLAN for PCs 1–2 on each switch</li>
  <li>VLAN 20 – VLAN for PCs 3–4 on each switch</li>
</ul>


<strong>From each switch CLI:</strong><br/>
<ul>
  <li>Define VLAN 10 and VLAN 20 and give them readable names</li>
  <li>Ensure the interface is up/up</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/MWRXN18.png" height="80%" width="80%" alt="IP Config"/>
 <br />

<br />
<br />

  
<h3>Step 4: Assigning Access Ports to VLANs</h3>

Assign each PC-facing switch port as an access port in the correct VLAN. <br/>

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

<h3>Step 6:IP Addressing for a Single Subnet</h3>

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

<h3>Step 7: Connectivity Testing Across VLANs and Switches</h3>

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

This lab demonstrated how to configure static VLANs and an 802.1Q trunk link between two Cisco switches in Packet Tracer, allowing eight hosts to share a single IP subnet while remaining logically segmented. By creating VLANs, assigning access ports, and enabling a trunk that carries tagged traffic for multiple VLANs, I built a small but realistic example of how enterprise switches implement network segmentation at Layer 2.


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

