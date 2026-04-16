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


<h3>Step 6: Verfiy the WAN Interfaces</h3>

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
      <img src="https://i.imgur.com/ye0FUkp.jpeg" height="250" width="300" alt="ipv6 int"/>
      <br><strong>sh ipv6 interface</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/HzvVFXQ.jpeg" height="250" width="300" alt="running-config"/>
      <br><strong>sh running-config</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/xRpm8W4.jpeg" height="250" width="300" alt="ipv6 brief "/>
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
<img src="https://i.imgur.com/CE72uaU.jpeg" height="80%" width="80%" alt="IPv6 Routing"/>
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
<img src="https://i.imgur.com/CE72uaU.jpeg" height="80%" width="80%" alt="IPv6 Hostnames"/>
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
      <img src="https://i.imgur.com/XyDkNEl.jpeg" height="250" width="300" alt="R1-LAN"/>
      <br><strong>R1-LAN</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/eohLhgx.jpeg" height="250" width="300" alt="R2-LAN"/>
      <br><strong>R2-LAN</strong>
    </td>
  </tr>
</table>
<p align="center">

<h3>Step 10: Verify LAN Connectivity</h3>

Use interface brief commands to confirm the LAN interfaces are active.<br/>

<ul>
  <li>Use show ipv6 interface brief to confirm Fa0/0 is up/up on both routers.</li>
  <li>Check that each router has a global unicast IPv6 address on Fa0/0.</li>
  <li>Verify that the link-local and global addresses are displayed correctly.</li>
  <li>Confirm that the LAN interfaces show as operational.</li>
  <li></li>
</ul>

<p align="center">
<img src="https://i.imgur.com/51iKgGd.jpeg" height="80%" width="80%" alt="Verify LAN Connectivity"/>
<br />
<br />

<h3>Step 10: Connectivity Testing (Inter-VLAN Routing)</h3>

First, verify local connectivity on both sides.<br/>

<ul>
  <li>From each VLAN in <strong>Network 1</strong>:
    <ul>
      <li>Ping another PC in the same VLAN.</li>
      <li>Ping the default gateway.</li>
    </ul>
  </li>
  <li>Repeat the same tests for Network 2</li>
</ul>

<table align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/m4i185g.jpeg" height="250" width="300" alt="Network 1 Ping"/>
      <br><strong>Network 1</strong>
    </td>
    <td align="center">
      <img src="https://i.imgur.com/6Wz7wrq.jpeg" height="250" width="300" alt="Network 2 Ping"/>
      <br><strong>Network 2</strong>
    </td>
  </tr>
</table>

<h3>Step 11: Test End-to-End Connectivity Between Networks</h3>

Finally, confirm static routing across the serial link.<br/>

<ul>
  <li>From <code>LAB‑R1</code>, ping <strong>LAB‑R2’s</strong> serial IP and vice versa to verify router‑to‑router reachability.</li>
  <li>Then test PC-to-PC pings across networks.</li>
  <li>Successful replies confirm static routing and gateways of last resort are working end-to-end.</li>
</ul>

<p align="center">
<img src="https://i.imgur.com/D3z0MsO.jpeg" height="60%" width="60%" alt="Router-Router Ping"/>
<p align="center">
Router-to-Router Ping Across Networks
<br/>

<p align="center">
<img src="https://i.imgur.com/VajHn2P.jpeg" height="60%" width="60%" alt="PC-PC Ping"/>
<p align="center">
PC-to-PC Ping Across Networks
<br/>
<br/>


<h3>Conclusion and Key Takeaways</h3>

This lab combined VLANs, trunk ports, router sub‑interfaces, serial links, and static routing to connect two separate multi‑VLAN networks. By configuring IP addressing, VLANs, gateways of last resort, and static routes on each router, I enabled reliable end‑to‑end communication between PCs on different networks while maintaining clear Layer 2 segmentation and Layer 3 control.

