
![[Router DHCP Configuration.png]]
## Prerequisites & Equipment

- Cisco Router (at least 2 GigabitEthernet ports)  
- Two switches (optional but recommended)  
- Ethernet cables  
- PC devices for LAN1 and LAN2  
- IP Subnetting:  
  - LAN1: `192.168.10.0/29` → Gateway: `192.168.10.1`  
  - LAN2: `192.168.20.0/29` → Gateway: `192.168.20.1`  

---

## Step 1: Physical Wiring

| Device      | Port                   | Connects To         |
|-------------|------------------------|----------------------|
| Router      | `GigabitEthernet 0/0`  | Switch for LAN1      |
| Router      | `GigabitEthernet 0/1`  | Switch for LAN2      |
| PC (LAN1)   | Ethernet               | Switch for LAN1      |
| PC (LAN2)   | Ethernet               | Switch for LAN2      |

---

## Step 2: Paste into Router CLI
enable  
configure terminal

! === Interface Configuration ===  
interface gigabitEthernet 0/0  
ip address 192.168.10.1 255.255.255.248  
no shutdown  
exit

interface gigabitEthernet 0/1  
ip address 192.168.20.1 255.255.255.248  
no shutdown  
exit

! === Exclude Gateway IPs from DHCP ===  
ip dhcp excluded-address 192.168.10.1  
ip dhcp excluded-address 192.168.20.1

! === DHCP Pool for LAN1 ===  
ip dhcp pool LAN1  
network 192.168.10.0 255.255.255.248  
default-router 192.168.10.1  
exit

! === DHCP Pool for LAN2 ===  
ip dhcp pool LAN2  
network 192.168.20.0 255.255.255.248  
default-router 192.168.20.1  
exit

---

## Step 3: Verify DHCP Configuration

Run the following commands to confirm DHCP is working:
show ip dhcp binding  
show ip dhcp pool

---
## Subnet /29 Breakdown (255.255.255.248)

- Total IPs: 8  
- Usable Hosts: 6  
- 1 reserved for router gateway  
- 5 available for DHCP clients per LAN  
---


