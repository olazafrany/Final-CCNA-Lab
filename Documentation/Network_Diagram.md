# Network Diagram

## Topology Overview
The network consists of three main parts:

1. **HQ (Headquarters):**
   - Two VLANs (IT and HR).
   - Core Switch (Multilayer) with DHCP for HR.
   - Access Switches (S1, S2) with EtherChannel.
   - HQ Router (Router-on-a-Stick).

2. **Branch:**
   - LAN network (`10.1.1.0/24`).
   - NAT (Static).
   - Branch Router with OSPF to HQ.

3. **ISP:**
   - Two ISPs (ISP1 and ISP2) with HSRP.
   - Redundant internet connection.

## Diagram
![Network Topology](Topology.png)

> Note: The image above shows the full network topology.
