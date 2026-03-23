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
<img src="https://i.imgur.com/wQhrCtr.jpeg" height="60%" width="60%" alt="Cabling Connections"/>
<p align="center">
Installation of Serial Module on Router
<br/>

<p align="center">
<img src="https://i.imgur.com/wQhrCtr.jpeg" height="60%" width="60%" alt="Cabling Connections"/>
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
<img src="https://i.imgur.com/N9MBkdk.jpeg" height="80%" width="80%" alt="Configure VLANs on Switch"/>
<br />
<br />

Verify VLAN membership with <code>show vlan brief</code>.
<br />

<p align="center">
<img src="https://i.imgur.com/uBof4px.jpeg" height="60%" width="60%" alt="VLAN Brief"/>
<br />
<br />

<h3>Step 5: Configure Trunk Port and Default VLAN on <code>LSW1</code></h3>

Configure the uplink from the switch:<code>LSW1</code> to the router as an 802.1Q trunk.<br />

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
<img src="https://i.imgur.com/mCwP4Ml.jpeg" height="80%" width="80%" alt="Switch Trunk"/>
<br />
<br />

