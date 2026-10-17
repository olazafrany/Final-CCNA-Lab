# IP Addressing Table

## VLANs
| VLAN ID | Name | Network | Gateway |
|---|---|---|---|
| 10 | IT | 192.168.10.0/24 | 192.168.10.1 |
| 20 | HR | 192.168.20.0/24 | 192.168.20.1 |

## Devices
| Device | Interface | IP Address | Subnet Mask | Description |
|---|---|---|---|---|
| HQ Router | Gig0/0/1.10 | 192.168.10.1 | 255.255.255.0 | Gateway for VLAN 10 |
| HQ Router | Gig0/0/1.20 | 192.168.20.1 | 255.255.255.0 | Gateway for VLAN 20 |
| HQ Router | Gig0/0/0 | 172.16.2.1 | 255.255.255.252 | WAN to Branch |
| Branch Router | Gig0/1 | 10.1.1.1 | 255.255.255.0 | LAN Gateway |
| Branch Router | Gig0/0 | 172.16.2.2 | 255.255.255.252 | WAN to HQ |
| Branch Router | Serial0/2/0 | 40.1.1.1 | 255.255.255.252 | WAN to ISP1 |
| Branch Router | Serial0/2/1 | 41.1.1.2 | 255.255.255.252 | WAN to ISP2 |
| ISP1 | Gig0/0/0 | 42.2.2.1 | 255.255.255.0 | LAN (HSRP) |
| ISP1 | Serial0/1/0 | 40.1.1.2 | 255.255.255.252 | WAN to Branch |
| ISP2 | Gig0/0/0 | 42.2.2.2 | 255.255.255.0 | LAN (HSRP) |
| ISP2 | Serial0/1/1 | 41.1.1.1 | 255.255.255.252 | WAN to Branch |
| Core Switch | VLAN 20 | 192.168.20.200 | 255.255.255.0 | Management |
| S1 Switch | VLAN 20 | 192.168.20.2 | 255.255.255.0 | Management |
| S2 Switch | VLAN 20 | 192.168.20.3 | 255.255.255.0 | Management |

## NAT Public IPs
| Inside Local | Inside Global | Description |
|---|---|---|
| 10.1.1.10 | 100.100.100.100 | Web Server |
| 10.1.1.20 | 8.8.8.8 | DNS Server |

## HSRP Virtual IP
| Group | Virtual IP | Active Router | Standby Router |
|---|---|---|---|
| 1 | 42.2.2.3 | ISP2 (42.2.2.2) | ISP1 (42.2.2.1) |

## DHCP Pool (Core Switch)
| Pool Name | Network | Default Router | DNS Server |
|---|---|---|---|
| HR_POOL | 192.168.20.0/24 | 192.168.20.1 | 8.8.8.8 |

## Excluded IPs from DHCP
- 192.168.20.1 to 192.168.20.5
- 192.168.20.200
