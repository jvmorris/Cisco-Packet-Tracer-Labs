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
<img src="https://i.imgur.com/gvTmnXc.jpeg" height="80%" width="80%" alt="Workspace Setup"/>
<br />
<br />

<h3>Step 2: Router Interface and VLAN Addressing Plan</h3>

Review router interface addressing tables for both LAB-R1 and LAB-R2 across all VLANs and serial links. <br/>

| Router / LAB-R1 / Interface | IPv4 Address / Subnet | VLAN |
|---|---|---|
| Serial 0/0/0 | 10.10.10.1 / 30 | n/a |
| Gi 0/1 | 172.168.1.1 / 24 | n/a |
| Gi0/1.1 | 192.168.100.1 / 24 | vlan 1 (default) |
| Gi0/1.10 | 192.168.10.1 / 28 | vlan10 (zone10) |
| Gi0/1.20 | 192.168.20.1 / 28 | vlan20 (zone20) |
| Gi0/1.30 | 192.168.30.1 / 28 | vlan30 (zone30) |

| Router / LAB-R2 / Interface | IPv4 Address / Subnet | VLAN |
|---|---|---|
| Serial 0/0/0 | 10.10.10.2 / 30 | n/a |
| Gi 0/1 | 172.168.2.1 / 24 | n/a |
| Gi0/1.1 | 192.168.200.1 / 24 | vlan 1 (default) |
| Gi0/1.110 | 192.168.110.1 / 28 | vlan110 (zone110) |
| Gi0/1.120 | 192.168.120.1 / 28 | vlan120 (zone120) |
| Gi0/1.130 | 192.168.130.1 / 28 | vlan130 (zone130) |
 
<h3>Step 3: Cabling All Devices</h3>

Build physical connections for both Networks.<br>

<ul>
  <li>Use copper straight-through cables for all  <strong>PC → Switch</strong> connections.</li>
  <li>Connect the switch to the router’s Ethernet interface <code>Gi0/1 → Gi0/1</code> on each side.</li>
  <li>Install serial WICs on both routers if needed, then connect LAB‑R1’s serial interface (Serial0/0/0) to LAB‑R2’s serial interface (Serial0/0/0) using a <strong>Serial DCE</strong> cable.</li>
  <li>Wait for all <strong>PC → Switch</strong> links to turn green to confirm physical connectivity.</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/I5G7BGr.jpeg" height="60%" width="60%" alt="Cabling Connections"/>
<p align="center">
Installation of Serial Module on Router
<br/>

<p align="center">
<img src="https://i.imgur.com/djd2mVw.jpeg" height="60%" width="60%" alt="Cabling Connections"/>
<p align="center">
All Devices Successfully Connected
<br/>
<br/>

<h3>Step 4: Configure VLANs and Access Ports on Switch:<code>LSW1</code></h3>

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
  <li>Fa0/1–Fa0/2 →  VLAN 10 PCs</li>
  <li>Fa0/9–Fa0/10 →  VLAN 20 PCs</li>
  <li>Fa0/17–Fa0/8 →  VLAN 30 PCs</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/R6Sj5IT.jpeg" height="80%" width="80%" alt="Configure VLANs on Switch"/>
<br />
<br />

Verify VLAN membership with <code>show vlan brief</code>.
<br />

<p align="center">
<img src="https://i.imgur.com/Xr03Xlh.jpeg" height="60%" width="60%" alt="VLAN Brief"/>
<br />
<br />

<h3>Step 5: Configure Trunk Port and Default VLAN on <code>LSW1</code></h3>

Configure the uplink from the switch:<code>LSW1</code> to the router as an 802.1Q trunk.<br />

<ul>
  <li>Interface Gi0/1 on the switch:</li>
    <ul>
      <li>Set encapsulation to <code>dot1q</code></li>
      <li>Set mode to <code>trunk</code></li>
      <li>Allow VLANs 10, 20, and 30 on the trunk</li>
    </ul>
    </li>
</ul>

<p align="center">
<img src="https://i.imgur.com/uzWx291.jpeg" height="80%" width="80%" alt="Switch Trunk"/>
<br />
<br />

<h3>Step 6: Configure Router Physical Interface</h3>

On <code>LAB-R1</code>, configure Ethernet sub-interfaces and the serrial interface<br />

<ul>
  <li>Assign IP addresses and subnet masks to the router’s GigabitEthernet sub‑interfaces for each VLAN according to the plan</li>
  <li>Configure the serial interface <code>Serial0/0/0</code> with the /30 link network between <code>LAB-R1</code> and <code>LAB-R2</code>
    <ul>
      <li>Bring it up with the command: <code>no shutdown</code></li>
    </ul>
  </li>
</ul>

Verify with <code>show ip int brief</code> that the router is configured properly.
<p align="center">
<img src="https://i.imgur.com/3iJgzda.jpeg" height="80%" width="80%" alt="Router Config"/>
<br />
<br />



<h3>Step 7: Configure PCs in <code>NETWORK1</code></h3>

<ul>
  <li>Click each PC → Desktop → IP Configuration.</li>
  <li>Set static IPs based on their VLAN assignment and the Plan in <strong>Step 2</strong>.
    <ul>
      <li><strong>VLAN 10 PCs (fa0/1-8)</strong>: IPs in 192.168.10.0/28 range | Gateway: 192.168.10.1
</li>
      <li><strong>VLAN 20 PCs (fa0/9-16)</strong>: IPs in 192.168.20.0/28 range | Gateway: 192.168.20.1
</li>
      <li><strong>VLAN 30 PCs (fa0/17-24)</strong>: IPs in 192.168.30.0/28 range | Gateway: 192.168.30.1</li>
    </ul>
    </li>
</ul>

<table align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/ye0FUkp.jpeg" height="250" width="300" alt="VLAN 10"/>
      <br><strong>VLAN 10</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/HzvVFXQ.jpeg" height="250" width="300" alt="VLAN 20"/>
      <br><strong>VLAN 20</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/xRpm8W4.jpeg" height="250" width="300" alt="VLAN 30"/>
      <br><strong>VLAN 30</strong>
    </td>
  </tr>
</table>
<p align="center">
PCs configured with VLAN-specific IPs and gateways, ready for connectivity testing.<br />

<h3>Step 8: Repeat Switch and Router Configuration for <code>NETWORK2</code></h3>

Repeat Steps 4-7 for Network 2.<br />

<code></code>

<ul>
  <li>Cable PCs to the <code>NETWORK2</code> switch and connect the switch to the Ethernet interface for <code>LAB-R2</code>.</li>
  <li>Create the same VLANs and assign access ports on the Network 2 switch.</li>
  <li>On <code>LAB‑R2</code>, configure GigabitEthernet sub‑interfaces and IPs for each VLAN, and verify the serial interface to <code>LAB‑R1</code> is up.</li>
  <li>Configure PC IP addresses and default gateways for Network 2 clients.</li>
</ul>

<table align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/6SCuMtp.jpeg" height="250" width="300" alt="VLAN 10"/>
      <br><strong>VLAN Config</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/aQ7A4Al.jpeg" height="250" width="300" alt="VLAN 20"/>
      <br><strong>Trunk Config</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/aKxF5v7.jpeg" height="250" width="300" alt="VLAN 30"/>
      <br><strong>PC Config</strong>
    </td>
  </tr>
</table>
<p align="center">
PCs configured with VLAN-specific IPs and gateways, ready for connectivity testing.<br />
