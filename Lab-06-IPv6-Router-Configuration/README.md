<h1>Lab #6: IPv6 Router Configuration and Address Management</h1>



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
  <li>Router: 2 x 2811</li>
  <li>Switch: 2 x 2960-24TT</li>
  <li>End Devices: 2 x PC</li>
</ul>

Arrange the devices so the routers are at the top, the switches are below each router, and the PCs are at the bottom.<br/>

<p align="center">
<img src="https://i.imgur.com/3N2ZxY0.jpeg" height="50%" width="50%" alt="Workspace Setup"/>
<br />
<br />
  
<h3>Step 2: Cabling All Devices</h3>

Build physical connections for both Networks.<br>

<ul>
  <li>Use copper straight-through cables for each <strong>PC → Switch</strong> connection.</li>
  <li>Connect the switch to the router’s Ethernet interface on each side.</li>
  <li>Install serial WICs on both routers if needed, then connect R1’s serial interface (Serial0/0/0) to R2’s serial interface (Serial0/0/1) using a <strong>Serial DCE</strong> cable.</li>
  <li>Wait for all <strong>PC → Switch</strong> links to turn green to confirm physical connectivity.</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/4SzQul2.jpeg" height="60%" width="60%" alt="Cabling Connections"/>
<br/>
<br/>

<h3>Step 3: Router Interface Addressing Plan </h3>

Review router interface addressing tables for both R1 and R2. <br/>

| Router: R1 / Interface | IPv6 Address / Subnet |
|---|---|
| FA 0/0 | 2001:C16C:0000:0002:0000:0000:0000:0000/64 |
| Serial 0/0/0 | 2001:C16C:0000:0001:0000:0000:0000:0001/64 |

| Router: R2 / Interface | IPv6 Address / Subnet |
|---|---|
| FA 0/0 | 2001:C16C:0000:0003:0000:0000:0000:0000/64 |
| Serial 0/0/1 | 2001:C16C:0000:0001:0000:0000:0000:0002/64 |


<h3>Step 4: Enabling IPv6 Routing</h3>

<ul>
  <li>Enter global configuration mode on both routers.</li>
  <li>Enable IPv6 unicast routing on R1 and R2 using the command <code>ipv6 unicast-routing</code>.</li>
</ul>


<h3>Step 5: Configure the WAN Interfaces</h3>

 Assign IPv6 addresses to the serial interfaces and enable the WAN link.<br/>
<ul>
  <li>On R1, configure Serial0/0/0 with the IPv6 WAN address.</li>
  <li>If R1 is the DCE side, set the clock rate.</li>
  <li>Use <code>no shutdown</code> to activate the interface.</li>
  <li>On R2, configure Serial0/0/1 with the matching IPv6 WAN address.</li>
  <li>Use no shutdown to bring the interface up.</li>
</ul>


<h3>Step 6: Verify the WAN Interfaces</h3>

Check that both serial interfaces are active, addressed correctly, and reporting the expected status.<br />

<ul>
  <li>Use <code>show ipv6 interface</code> to verify the global and link-local addresses.</li>
  <li>Use <code>show running-config</code> to confirm the IPv6 address was added correctly to the serial interface.</li>
  <li>Use <code>show ipv6 interface brief</code> to confirm the interfaces are up/up.</li>
  <li>Make sure the serial link is operational before moving on.</li>
</ul>

<table align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/gsxBBxM.jpeg" height="250" width="300" alt="ipv6 int"/>
      <br><strong>sh ipv6 interface</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/RqESsYW.jpeg" height="250" width="300" alt="running-config"/>
      <br><strong>sh running-config</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/eqzYUtj.jpeg" height="250" width="300" alt="ipv6 brief "/>
      <br><strong>sh ipv6 interface brief</strong>
    </td>
  </tr>
</table>
<br />
<br />

<h3>Step 7: Verify IPv6 Routing and Test Connectivity</h3>

Confirm that IPv6 routes are present and test communication between the two routers.<br />

<ul>
  <li>Use <code>show ipv6 route</code> to verify the connected and local routes on the router.</li>
  <li>Use <code>ping ipv6</code> command to ping R2 to the IPv6 address of R1's serial interface to test IPv6 connectivity between the two routers.</li>
  <li>Confirm the router configuration matches the addressing plan.</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/JiYunA2.jpeg" height="60%" width="60%" alt="IPv6 Routing"/>
<br />
<br />

<h3>Step 8: Configure IPv6 Hostnames</h3>

Assign IPv6 hostnames to the router addresses and test name-based connectivity.<br />

<ul>
  <li>Use the <code>ip host</code> command to map the WAN hostname to R1’s serial IPv6 address.</li>
  <li>Use the <code>ip host</code> command to map the WAN hostname to R2’s serial IPv6 address.</li>
  <li>Test the hostname by using the ping command with the assigned name.</li>
  <li>Confirm the hostname resolves to the correct IPv6 address.</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/P93UJNX.jpeg" height="60%" width="60%" alt="IPv6 Hostnames"/>
<br />
<br />

<h3>Step 9: Configure the LAN Interfaces</h3>

Configure the FastEthernet interfaces on both routers using the EUI-64 option.<br />

<ul>
  <li>On R1, enter <code>int fa0/0</code>.</li>
  <li>Configure the IPv6 LAN prefix using <code>ipv6 address 2001:C16C:0:2::/64 eui-64</code>.</li>
  <li>Use <code>no shutdown</code> to enable the interface.</li>
  <li>Repeat the process on R2 using <code>ipv6 address 2001:C16C:0:3::/64 eui-64</code>.</li>
  <li>Verify that both LAN interfaces come up successfully.</li>
</ul>

<table align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/rdzOlx4.jpeg" height="250" width="300" alt="R1-LAN"/>
      <br><strong>R1-LAN</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/vwRlR0W.jpeg" height="250" width="300" alt="R2-LAN"/>
      <br><strong>R2-LAN</strong>
    </td>
  </tr>
</table>
<p align="center">

<h3>Step 10:Verify LAN Connectivity and Final Routes</h3>

Use interface and routing commands to confirm the LAN interfaces are active and the full IPv6 topology is working.<br/>

<ul>
  <li>Use <code>show ipv6 interface brief</code> to confirm the LAN interfaces are up/up.</li>
  <li>Check that each router has a global unicast IPv6 address on Fa0/0.</li>
  <li>Use <code>show ipv6 route</code> to confirm the LAN networks appear as connected routes.</li>
  <li>Verify that all directly attached IPv6 networks are present in the routing table.</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/VNeTdSr.jpeg" height="80%" width="80%" alt="Verify LAN Connectivity"/>
<br />
<br />



<h3>Conclusion and Key Takeaways</h3>

This lab provided hands-on experience configuring IPv6 on Cisco routers, including enabling IPv6 routing, assigning WAN and LAN addresses, and verifying interface status. It also reinforced the use of routing tables, interface checks, hostname mappings, and ping tests to confirm end-to-end connectivity across the network.



