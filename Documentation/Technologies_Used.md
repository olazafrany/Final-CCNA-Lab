# Technologies Used

## 1. VLANs and Trunking
- **VLAN 10 (IT):** For IT department devices.
- **VLAN 20 (HR):** For HR department devices.
- **Trunking (802.1q):** Used between switches and the router for carrying multiple VLANs.

## 2. EtherChannel
- **PAgP (Port Aggregation Protocol):** Used between Core Switch and S2 (`mode desirable`).
- **Static (On):** Used between Core Switch and S1 (`mode on`).
- **Purpose:** Increase bandwidth and provide redundancy.

## 3. Inter-VLAN Routing (Router-on-a-Stick)
- Configured on HQ Router using sub-interfaces (`Gig0/0/1.10` and `Gig0/0/1.20`).
- Allows communication between VLAN 10 and VLAN 20.

## 4. OSPF (Single Area)
- Used between HQ Router and Branch Router.
- Area 0 (Backbone).
- Advertises internal networks (`192.168.10.0/24`, `192.168.20.0/24`, `10.1.1.0/24`, `172.16.2.0/30`).

## 5. NAT (Network Address Translation)
- **Static NAT:** Maps internal servers to public IPs (`10.1.1.10` → `100.100.100.100`, `10.1.1.20` → `8.8.8.8`).
- **NAT Overload (PAT):** Allows all Branch devices to access the internet using one public IP.
- Applied on Branch Router.

## 6. ACL (Access Control List)
- **Extended ACL 101:** Blocks ICMP (Ping) from IT VLAN (`192.168.10.0/24`) to Web Server (`10.1.1.10`).
- Applied on HQ Router (`Gig0/0/0 out`).

## 7. HSRP (Hot Standby Router Protocol)
- Configured between ISP1 and ISP2.
- Virtual IP: `42.2.2.3`
- Provides redundancy for the internet connection.

## 8. Port Security
- Configured on Branch Switch (`Fa0/15`).
- Maximum MAC addresses: 1
- Violation mode: Shutdown
- MAC address sticky enabled.
- Prevents unauthorized devices from connecting.

## 9. DHCP
- Configured on Core Switch for HR VLAN.
- Pool name: `HR_POOL`
- Excluded IPs: `192.168.20.1-5`, `192.168.20.200`

## 10. Routing (Static and Default)
- **Default Route:** On Branch Router, pointing to ISPs (`0.0.0.0/0` via Serial0/2/0 and Serial0/2/1).
- **Floating Static Route:** Backup route via Serial0/2/1 with AD 5.

## 11. Device Security
- **Enable Secret:** `class` (Encrypted).
- **Console Password:** Configured.
- **VTY Password:** `cisco` (For Telnet access).
- **Service Password-Encryption:** Enabled.
- **Banner MOTD:** `hello`
- Applied on HQ Router.

## 12. Technologies Studied (Not Implemented in This Lab)
- VTP Protocol
- RIP / EIGRP
- IPv6 Routing
- Standard ACL
- Frame Relay
- Point-to-Point Protocol (PPP)
- Wireless Network
- DNS Server (Configured via NAT)
- CDP
- Backup Router Configurations
- Recover Router Password
- MAC Flooding (Static)
