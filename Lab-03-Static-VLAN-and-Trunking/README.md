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
<img src="https://i.imgur.com/56HX6E9.jpeg" height="80%" width="80%" alt="Workspace Setup"/>
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
<img src="https://i.imgur.com/2josOH9.jpeg" height="80%" width="80%" alt="Cabling Connections"/>
<br/>
<br/>


<h3>Step 3: Configuring VLANs on Both Switches</h3>

Open the CLI for each switch and configure the VLANs and access ports.<br/>

<strong>VLAN Configuration:</strong><br/>
<ul>
  <li>Create VLAN 10 and VLAN 20
  <li>Assign Access Ports to VLANs
     <ul>
        <li>Fa0/1-2: access ports to VLAN 10/li>
        <li>Fa0/3-4: access ports to VLAN 20/li>
        <li>Optionally shut down unused ports Fa0/5-23>
    </ul>
  </li>
  <li>Configure the 802.1Q Trunk</li>
</ul>




<div style="display: flex; justify-content: center; gap: 20px;">

  <img src="https://i.imgur.com/dwu7LNx.png" height="45%" width="45%" alt="VLAN Configuration"/>

  <img src="https://i.imgur.com/j8qFtfX.png" height="45%" width="45%" alt="VLAN Configuration"/>

</div>

<br />
<br />

  
<h3>Step 4: PC IP Configuration</h3>

Assign IP addresses so all eight PCs share the same IPv4 subnet while remaining logically separated by VLANs.

<strong>IP Address Assigned:</strong><br/>
<ul>
  <li>PC 0: 192.168.21.11</li>
  <li>PC 1: 192.168.21.12</li>
  <li>PC 2: 192.168.21.13</li>
  <li>PC 3: 192.168.21.14</li>
  <li>PC 4: 192.168.21.15</li>
  <li>PC 5: 192.168.21.16</li>
  <li>PC 6: 192.168.21.17</li>
  <li>PC 7: 192.168.21.18</li>
</ul>

<strong>Subnet Mask Assigned:</strong> 255.255.255.0<br/>

<p align="center">
<img src="https://i.imgur.com/qIp1QdI.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

<h3>Step 5: Connect the Switches Together</h3>

<ul>
  <li>From the <strong>Connections</strong> toolbar, select a copper straight-through cable</li>
  <li>Port Used: Fa0/24</li>
  <li>Wait until the inter-switch link turns green on both ends to confirm a good physical connection</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/Uqp6RnK.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

<h3>Step 6:Add VLAN Bubbles and Labels</h3>

Visually document the VLAns in the topology.

<ul>
  <li>Use the <strong>Draw Ellipse</strong> in the drawing tools to create shaded "bubbles" to visualize the VLANS on each switch.</li>
  <li>Use the <strong> Place Note</strong> to add text labels: "VLAN 10" and "VLAN 20" inside each bubble.
</ul>

<p align="center">
<img src="https://i.imgur.com/PA00wtD.png" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

<h3>Step 7: Connectivity Testing Across VLANs and Switches</h3>

Verify correct behavior for same-VLAN and different-VLAN traffic.<br/>


<strong>Successful pings:</strong><br/>
<ul>
  <li>From each PC, ping the router’s LAN IP: < strong>192.168.21.1</strong></li>
  <li>Ping between PCs</li>
  <li>Confirm all hosts receive successful replies</li>
</ul>

<div style="display: flex; justify-content: center; gap: 20px;">

  <img src="https://i.imgur.com/NS5gA1w.jpeg" height="45%" width="45%" alt="VLAN Configuration"/>

  <img src="https://i.imgur.com/L9OYMUF.jpeg" height="45%" width="45%" alt="VLAN Configuration"/>

</div>

<strong>Unsuccessful pings:</strong><br/>
<ul>
  <li>One VLAN 10 PC -> one VLAN 20 PC (no inter-VLAN routing confirmed)
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

