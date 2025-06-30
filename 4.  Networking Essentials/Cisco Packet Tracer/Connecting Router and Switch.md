
# Full Cisco Packet Tracer Setup: Two Networks with Subnetting and Manual IP Configuration
![[Connecting Router and Switch.png]]

---
## 1. Subnetting Plan

We will use the subnet mask **255.255.255.248 (/29)** for both networks.

Each /29 subnet provides:
- Total IP addresses: 8
- Usable IP addresses: 6
- 1 Network address and 1 Broadcast address

### Network A: 192.168.1.0/29
- Network address: 192.168.1.0
- Broadcast address: 192.168.1.7
- Usable IP range: 192.168.1.1 to 192.168.1.6

### Network B: 192.168.2.0/29
- Network address: 192.168.2.0
- Broadcast address: 192.168.2.7
- Usable IP range: 192.168.2.1 to 192.168.2.6
---
## 2. Device IP Assignment

### Network A

| Device       | IP Address     | Subnet Mask         | Default Gateway |
|--------------|----------------|----------------------|-----------------|
| PC0          | 192.168.1.1    | 255.255.255.248      | 192.168.1.6     |
| PC1          | 192.168.1.2    | 255.255.255.248      | 192.168.1.6     |
| PC2          | 192.168.1.5    | 255.255.255.248      | 192.168.1.6     |
| Router G0/0  | 192.168.1.6    | 255.255.255.248      | N/A             |

### Network B

| Device       | IP Address     | Subnet Mask         | Default Gateway |
|--------------|----------------|----------------------|-----------------|
| PC4          | 192.168.2.1    | 255.255.255.248      | 192.168.2.6     |
| PC5          | 192.168.2.2    | 255.255.255.248      | 192.168.2.6     |
| PC6          | 192.168.2.3    | 255.255.255.248      | 192.168.2.6     |
| PC7          | 192.168.2.4    | 255.255.255.248      | 192.168.2.6     |
| Router G0/1  | 192.168.2.6    | 255.255.255.248      | N/A             |


---
## 3. Cabling Requirements

| Connection             | Cable Type        |
|------------------------|-------------------|
| Router G0/0 to Switch A| Straight-through  |
| Router G0/1 to Switch B| Straight-through  |
| Switch A to PCs (A)    | Straight-through  |
| Switch B to PCs (B)    | Straight-through  |

---
## 4. Router CLI Configuration

1. Click on the router and go to the CLI tab
2. Enter the following commands:

```bash
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.1.6 255.255.255.248
no shutdown
exit

interface gigabitEthernet 0/1
ip address 192.168.2.6 255.255.255.248
no shutdown
exit

end
write memory

