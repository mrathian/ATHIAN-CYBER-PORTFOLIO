# 🖧 DHCP Implementation using Cisco Packet Tracer

**Project Title**: Dynamic Host Configuration Protocol (DHCP) Server Setup  
**Tool**: Cisco Packet Tracer  
**Level**: Beginner Networking Lab  

## 📋 Objective
Configure a router as a DHCP server so that client PCs automatically receive IP addresses, default gateway, and DNS settings without manual configuration.

## 🛠️ Network Topology
- 1 Router (acting as DHCP Server)
- 1 Switch
- 3–4 PCs

**Network Details**:
- LAN: 192.168.1.0/24
- Router Interface (Gi0/0): 192.168.1.1
- DHCP Pool: 192.168.1.10 – 192.168.1.100
- Default Gateway: 192.168.1.1
- DNS Server: 8.8.8.8

## 🔧 Key Configuration Commands (Router CLI)

```bash
enable
configure terminal

! Exclude router's own IP from the pool
ip dhcp excluded-address 192.168.1.1 192.168.1.9

! Create DHCP pool
ip dhcp pool MYPOOL
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 8.8.8.8
exit

! Configure router interface
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit

end
write memory
