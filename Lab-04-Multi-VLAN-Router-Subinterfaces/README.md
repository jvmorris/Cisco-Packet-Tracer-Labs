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
  <li>Switch: 1 x 3560-24PS</li>
  <li>End Devices: 6 x PC (PC1 - PC6) </li>
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

<div style="display: flex; justify-content: center; gap: 15px;">
  <div style="text-align: center;">
    <img src="https://i.imgur.com/6SCuMtp.jpeg" height="200px" width="250px" alt="VLAN 10 PC Configuration"/>
    <p><strong>VLAN 10</strong></p>
  </div>
  <div style="text-align: center;">
    <img src="https://i.imgur.com/aQ7A4Al.jpeg" height="200px" width="250px" alt="VLAN 20 PC Configuration"/>
    <p><strong>VLAN 20</strong></p>
  </div>
  <div style="text-align: center;">
    <img src="https://i.imgur.com/aKxF5v7.jpeg" height="200px" width="250px" alt="VLAN 30 PC Configuration"/>
    <p><strong>VLAN 30</strong></p>
  </div>
</div>
<br />



<p align="center">
<img src="https://i.imgur.com/JtEWhFt.jpeg" height="80%" width="80%" alt="Workspace Setup"/>
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
<img src="https://i.imgur.com/wQhrCtr.jpeg" height="60%" width="60%" alt="Cabling Connections"/>
<br/>
<br/>

<h3>Step 4: Configure VLANs and Access Ports on the Switch</h3>

Open the CLI on the switch and map the access ports to the correct VLANs.<br/>

<strong>VLAN Configuration</strong><br/>
<ul>
  <li>Create and name the VLANs:
     <ul>
        <li>VLAN 10 - <code>Zone 10</code> </li>
        <li>VLAN 20 - <code>Zone 20</code></li>
        <li>VLAN 30 - <code>Zone 30</code></li>
    </ul>
  </li>
</ul>

<strong>Access Port Assignments</strong>:<br/>
<ul>
  <li>Fa0/1–Fa0/2 → access ports in VLAN 10 (PC1–PC2)</li>
  <li>Fa0/3–Fa0/4 → access ports in VLAN 20 (PC3–PC4)</li>
  <li>Fa0/5–Fa0/6 → access ports in VLAN 30 (PC5–PC6)</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/N9MBkdk.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

Verify with <code>show vlan brief</code> that each port is in the expected VLAN and take a screenshot of the output.
<br />

<p align="center">
<img src="https://i.imgur.com/uBof4px.jpeg" height="60%" width="60%" alt="Ping Testing"/>
<br />
<br />

<h3>Step 5: Configure the Switch Trunk to the Router</h3>

Configure the uplink from the switch to the router as an 802.1Q trunk.<br />

<ul>
  <li>Interface Fa0/24 on the switch:</li>
    <ul>
      <li>Set encapsulation to <code>dot1q</code></li>
      <li>Set mode to <code>trunk</code></li>
      <li>Allow VLANs 10, 20, and 30 on the trunk</li>
    </ul>
    </li>
</ul>

<p align="center">
<img src="https://i.imgur.com/mCwP4Ml.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />


<h3>Step 6: Configure Router Physical Interface</h3>

On the router, configure the main interface facing the switch:<br />

<ul>
  <li>Enter configuration mode and select Gi0/1</li>
  <li>Assign the native network address and bring the interface up:
    <ul>
      <li><strong>IP address:</strong> 172.168.1.1 /24</li>
      <li>Command: <code>no shutdown</code></li>
    </ul>
    </li>
</ul>

<p align="center">
<img src="https://i.imgur.com/PNIgqpT.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />


<h3>Step 7: Configure Native VLAN Sub‑Interface and Define VLANs on Router</h3>

With Gi0/1 up and connected to the switch, create the native sub‑interface and define the VLANs on the router.<br/>

Native sub‑interface <strong>(VLAN 1)</strong>:<br/>
<ul>
  <li>Create sub‑interface <code>Gi0/1.1</code></li>
  <li>Configure 802.1Q encapsulation with VLAN 1 as the native VLAN</li>
  <li>Assign the default gateway IP for the native VLAN</li>
</ul>

<strong>VLAN Configuration:</strong><br/>
<ul>
  <li>Create and name the VLANs
     <ul>
        <li>VLAN 10 - <code>Zone 10</code> </li>
        <li>VLAN 20 - <code>Zone 20</code></li>
        <li>VLAN 30 - <code>Zone 30</code></li>
    </ul>
  </li>
</ul>

<p align="center">
<img src="https://i.imgur.com/VxiwfGm.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />
The router is ready for the remaining sub‑interfaces (for VLANs 10, 20, and 30), and the switch can map access ports to those VLANs in later steps.
<br />


<h3>Step 8: Configure Router Sub‑Interfaces for Each VLAN</h3>

With the native sub‑interface and VLANs defined, configure 802.1Q sub‑interfaces on <strong>Gi0/1</strong> to provide a default gateway for each VLAN.<br/>

<strong>Create 802.1Q sub‑interfaces</strong>:<br/>

<ul>
  <li>For <strong>VLAN 10</strong>:
    <ul>
      <li>Interface: <code>Gi0/1.10</code></li>
      <li>Encapsulation: <code>dot1Q 10</code></li>
      <li>IP address: <code>192.168.10.1 /24</code></li>
    </ul>
  </li>
  <li>For <strong>VLAN 20</strong>:
    <ul>
      <li>Interface: <code>Gi0/1.20</code></li>
      <li>Encapsulation: <code>dot1Q 20</code></li>
      <li>IP address: <code>192.168.20.1 255.255.255.240</code></li>
    </ul>
  </li>
  <li>For <strong>VLAN 30</strong>:
     <ul>
      <li>Interface: <code>Gi0/1.30</code></li>
      <li>Encapsulation: <code>dot1Q 30</code></li>
      <li>IP address: <code>192.168.30.1 255.255.255.240</code></li>
    </ul>
  </li>
</ul>

<p align="center">
<img src="https://i.imgur.com/fJqOiU9.jpeg" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />
After creating the sub‑interfaces, I set the router hostname to LAN-A-Router and saved the running configuration to startup configuration so the router‑on‑a‑stick setup persists across reboots.
<br />

<h3>Step 9: Connectivity Testing (Inter-VLAN Routing)</h3>

Verify that the router sub‑interfaces are correctly routing between VLANs.<br/>

<strong>Successful pings:</strong><br/>
<ul>
  <li>From a <strong>VLAN 10 PC</strong>, ping:
    <ul>
      <li>Its own gateway: <code>192.168.10.1</code></li>
      <li>PC ↔ PC ping in VLAN 10</li>
    </ul>
  </li>
</ul>

<strong>Unsuccessful pings:</strong><br/>
<ul>
  <li>From a <strong>VLAN 10 PC</strong>, ping:
    <ul>
      <li>A VLAN 20 PC: <code>192.168.20.3</code></li>
      <li>A VLAN 30 PC: <code>192.168.30.5</code></li>
    </ul>
  </li>
</ul>

<p align="center">
<img src="https://i.imgur.com/z5WCE9O.png" height="80%" width="80%" alt="Ping Testing"/>
<br />
<br />

<h3>Conclusion and Key Takeaways</h3>

This lab demonstrated how to use VLANs and router sub‑interfaces to create multiple isolated IP networks on a single switch while still allowing controlled communication between them. By combining static VLAN configuration, an 802.1Q trunk, and router‑on‑a‑stick sub‑interfaces, I built a small multi‑VLAN environment that mirrors how enterprises segment traffic and route between internal networks on shared infrastructure.


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

