<h1>Lab #4: Multiple VLANs with Router Sub‑Interfaces in Cisco Packet Tracer</h1>



<h2>Description</h2>
Configure multiple VLANs and router sub‑interfaces in Cisco Packet Tracer by assigning unique IP subnets per VLAN, enabling 802.1Q encapsulation on a router‑on‑a‑stick link, and verifying inter‑VLAN connectivity between hosts.
<br />


<h2>Utilities Used</h2>

- <b>Cisco Packet Tracer</b>
- <b>Command Prompt</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2></h2>
<h3>Step 1: Workspace Setup</h3>

Create the topology shown in the diagram:  <br/>

<strong>Devices Used:</strong><br/>
<ul>
  <li>Router: 1 x 2901</li>
  <li>Switch: 2 x 3560-24PS</li>
  <li>End Devices: 6 x PC (PC1 - PC6) </li>
</ul>

<p align="center">
<img src="https://i.imgur.com/56HX6E9.jpeg" height="80%" width="80%" alt="Workspace Setup"/>
<br />
<br />

<h3>Step 2: IP Addressing and VLAN Plan</h3>

Pending Description:  <br/>

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
      <li>PC1: 192.168.10.2/24 - Fa0/1</li>
      <li>PC2: 192.168.10.3/24 - Fa0/2</li>
    </ul>
  </li>
   <li>VLAN 20:
    <ul>
      <li>PC3: 192.168.20.3/24 - Fa0/3</li>
      <li>PC4: 192.168.20.4/24 - Fa0/4</li>
    </ul>
  </li>
  <li>VLAN 30:
    <ul>
      <li>PC5: 192.168.30.5/24 - Fa0/5</li>
      <li>PC6: 192.168.30.6/24 - Fa0/6</li>
    </ul>
  </li>
</ul>

Each PC’s default gateway will be the matching router sub‑interface IP.<br>

<p align="center">
<img src="https://i.imgur.com/56HX6E9.jpeg" height="80%" width="80%" alt="Workspace Setup"/>
<br />
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
<img src="https://i.imgur.com/2josOH9.jpeg" height="80%" width="80%" alt="Cabling Connections"/>
<br/>
<br/>


<h3>Step 4: Configure Router Physical Interface</h3>

On the router, configure the main interface facing the switch:<br />

<ul>
  <li>Enter configuration mode and select Gi0/1</li>
  <li>Assign the native network address and bring the interface up:
    <ul>
      <li><strong>IP address:</strong> 172.168.1.1 /24</li>
      <li>Command: <strong>no shutdown</strong></li>
    </ul>
    </li>
</ul>



<p align="center">
<img src="https://i.imgur.com/qIp1QdI.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

  
<h3>Step 5: Configuring VLANs and Assign Access Ports</h3>

Open the CLI for VLAN configuration for the Switch in the topology.<br/>

<strong>VLAN Configuration:</strong><br/>
<ul>
  <li>Create and name the VLANs
     <ul>
        <li>VLAN 10 - <strong> Zone 10</strong> </li>
        <li>VLAN 20 - <strong> Zone 20</strong></li>
        <li>VLAN 30 - <strong> Zone 30</strong></li>
    </ul>
  </li>
  <li>Assign Access Ports to VLANs
     <ul>
        <li>Fa0/1-2: access ports to VLAN 10</li>
        <li>Fa0/3-4: access ports to VLAN 20</li>
        <li>Fa0/5-6: access ports to VLAN 30</li>
    </ul>
  </li>
</ul>




<div style="display: flex; justify-content: center; gap: 20px;">

  <img src="https://i.imgur.com/dwu7LNx.png" height="45%" width="45%" alt="VLAN Configuration"/>

  <img src="https://i.imgur.com/j8qFtfX.png" height="45%" width="45%" alt="VLAN Configuration"/>

</div>

<br />
<br />



<h3>Step 6: Connect the Switches Together</h3>

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

Visually document the VLANs in the topology.

<ul>
  <li>Use the <strong>Draw Ellipse</strong> in the drawing tools to create shaded "bubbles" to visualize the VLANS on each switch.</li>
  <li>Use the <strong> Place Note</strong> to add text labels: "VLAN 10" and "VLAN 20" inside each bubble.</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/PA00wtD.png" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

<h3>Step 7: Connectivity Testing Across VLANs and Switches</h3>

Verify correct behavior for same-VLAN and different-VLAN traffic.<br/>


<strong>Successful pings:</strong><br/>
<ul>
  <li>PC<->PC on Switch A</li>
  <li>PC<->PC on Switch B</li>
  <li>One VLAN 10 PC <-> one VLAN 10 PC (across trunk)</li>
</ul>

<div style="display: flex; justify-content: center; gap: 16px; flex-wrap: wrap;">

  <div style="text-align: center;">
    <img src="https://i.imgur.com/6IQqBGM.png" height="60%" width="60%" alt="VLAN Creation"/>
    <p><strong>Switch A PC<->PC</strong></p>
  </div>

  <div style="text-align: center;">
    <img src="https://i.imgur.com/v2HpFZi.png" height="60%" width="60%" alt="Access Port Assignment"/>
    <p><strong>Switch B PC<->PC</strong></p>
  </div>

  <div style="text-align: center;">
    <img src="https://i.imgur.com/QJXifbR.png" height="60%" width="60%" alt="Trunk Configuration"/>
    <p><strong>VLAN 10 PC<->VLAN 10 PC</strong></p>
  </div>

</div>

<strong>Unsuccessful pings:</strong><br/>
<ul>
  <li>One VLAN 10 PC <-> one VLAN 20 PC (no inter-VLAN routing confirmed)</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/Ahs9u5w.png" height="60%" width="60%" alt="Ping Testing"/>
<p align="center">
<strong>PC1</strong> (VLAN 10)<-> <strong>PC6</strong> (VLAN 20) 
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

