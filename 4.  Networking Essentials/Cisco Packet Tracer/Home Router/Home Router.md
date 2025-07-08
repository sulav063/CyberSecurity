# 🌐 Static Routing Configuration - Full Setup (Router0 ↔ Router1 ↔ Server)

This configuration connects:
- Router0 to a home router and internal network (Laptops, PCs, VoIP via DHCP)
- Router1 to Router0 and a Server with static IP
- Static routing is used between Router0 and Router1
- DHCP is enabled on Laptops and PCs via WPC300N
![[HomeRouter.png]]

---

###  Router0 Configuration

```bash
enable
configure terminal

# Configure interface to internal LAN (e.g., PCs/Laptops/VoIP via WPC300N)
interface gigabitEthernet0/1
ip address 200.1.1.1 255.255.255.252
no shutdown
exit

# Configure interface to Router1 (via home router or direct connection)
interface gigabitEthernet0/0
ip address 112.100.10.1 255.255.255.252
no shutdown
exit

# Add static route to Server network through Router1
ip route 10.10.10.0 255.255.255.252 112.100.10.2
exit
```

---

###  Router1 Configuration

```bash
enable
configure terminal

# Interface facing Router0
interface gigabitEthernet0/0
ip address 112.100.10.2 255.255.255.252
no shutdown
exit

# Interface facing Server
interface gigabitEthernet0/1
ip address 10.10.10.1 255.255.255.252
no shutdown
exit

# Add static route to Router0's internal network
ip route 200.1.1.0 255.255.255.252 112.100.10.1
exit
```

---

### Server Configuration

Go to: **Desktop > IP Configuration**  
Set:
- IP Address: `10.10.10.2`
- Subnet Mask: `255.255.255.252`
- Default Gateway: `10.10.10.1`

---
### Home router Configuration

![[wirelessrouter0.png]]

### Laptop Config 

Use WPC300N and before using it turn off the laptop

![[laptop.png]]
---

### PC and Laptop Configuration (via DHCP)

Use **WPC300N** wireless router connected to Router0 G0/1.

Steps:
1. Click each **PC or Laptop**
2. Go to **Desktop > IP Configuration**
3. Select **DHCP**
4. IP should auto-assign from `200.1.1.0/30` network

---

##  Verification Steps

### 1. Check Interface Status

```bash
show ip interface brief
```

Expected outputs:
- Router0 G0/0 and G0/1: `up up`
- Router1 G0/0 and G0/1: `up up`

---

### 2. Ping Tests

- From PC → Server
```bash
ping 10.10.10.2
```

- From Server → PC
```bash
ping 200.1.1.X  # Replace X with actual IP assigned to PC
```

- From Router0 → Router1
```bash
ping 112.100.10.2
```

- From Router1 → Router0
```bash
ping 112.100.10.1
```

---

## IP Address Summary

| Device        | Interface        | IP Address       | Subnet Mask         | Notes                         |
|---------------|------------------|------------------|----------------------|-------------------------------|
| Router0       | G0/0 (to Router1)| 112.100.10.1     | 255.255.255.252      | WAN link to Router1           |
| Router0       | G0/1 (to WPC300N)| 200.1.1.1        | 255.255.255.252      | Internal LAN                  |
| Router1       | G0/0 (to Router0)| 112.100.10.2     | 255.255.255.252      | WAN link to Router0           |
| Router1       | G0/1 (to Server) | 10.10.10.1       | 255.255.255.252      | Server LAN                    |
| Server        | —                | 10.10.10.2       | 255.255.255.252      | Static IP                     |
| PC/Laptop     | via DHCP         | 200.1.1.x        | 255.255.255.252      | Assigned by WPC300N (DHCP)    |



