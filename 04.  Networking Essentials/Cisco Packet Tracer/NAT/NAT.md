# 🌐 Cisco Packet Tracer Full Setup – DHCP, NAT, Static Routing

![[04.  Networking Essentials/Cisco Packet Tracer/NAT/NAT.png]]

---

# 🌐 Cisco Packet Tracer Full Setup – DHCP, NAT, Static Routing

## 🧭 Network Topology Overview

**IP Schema Summary:**

| Network         | Subnet           | Router Interface |
|------------------|------------------|------------------|
| LAN1             | 10.0.0.0/29       | Router0 Gig0/1   |
| LAN2             | 20.0.0.0/29       | Router1 Gig0/1   |
| WAN (Router Link) | 200.150.10.0/30  | R0:Gig0/0 ↔ R1:Gig0/0 |
| R0 ↔ Server0     | 60.0.0.0/29       | Router0 Gig0/2   |
| R1 ↔ Server1     | 50.0.0.0/29       | Router1 Gig0/2   |

---

```bash
Router 0 Configuration (R0)
enable
conf t

interface gig0/0
ip address 200.150.10.1 255.255.255.252
no shutdown
exit

interface gig0/1
ip address 10.0.0.1 255.255.255.248
no shutdown
exit

interface gig0/2
ip address 60.0.0.1 255.255.255.248
no shutdown
exit

### DHCP Setup for LAN1
ip dhcp excluded-address 10.0.0.1
ip dhcp pool LAN1
network 10.0.0.0 255.255.255.248
default-router 10.0.0.1

Static Routes
ip route 20.0.0.0 255.255.255.248 200.150.10.2
ip route 50.0.0.0 255.255.255.248 200.150.10.2

### NAT Configuration for LAN1
access-list 1 permit 10.0.0.0 0.0.0.7

interface gig0/1
ip nat inside
exit

interface gig0/2
ip nat outside
exit

ip nat inside source list 1 interface gig0/2 overload


```

```bash
🧱 Router 1 Configuration (R1)
enable
conf t

interface gig0/0
ip address 200.150.10.2 255.255.255.252
no shutdown
exit

interface gig0/1
ip address 20.0.0.1 255.255.255.248
no shutdown
exit

interface gig0/2
ip address 50.0.0.1 255.255.255.248
no shutdown
exit

### DHCP Setup for LAN2
ip dhcp excluded-address 20.0.0.1
ip dhcp pool LAN2
network 20.0.0.0 255.255.255.248
default-router 20.0.0.1

### Static Routes
ip route 10.0.0.0 255.255.255.248 200.150.10.1
ip route 60.0.0.0 255.255.255.248 200.150.10.1

🔁 NAT Configuration for LAN2
access-list 1 permit 20.0.0.0 0.0.0.7

interface gig0/1
ip nat inside
exit

interface gig0/2
ip nat outside
exit

ip nat inside source list 1 interface gig0/2 overload

```

---
## 💻 PC Setup (Dynamic IP via DHCP)

- Go to: **PC → Desktop → IP Configuration**
    
- Set to: `DHCP`
    

### ✅ DHCP Expected IP Assignments

|PC|Network|Expected IP Range|Gateway|
|---|---|---|---|
|PC0|LAN1|10.0.0.2–10.0.0.6|10.0.0.1|
|PC1|LAN1|10.0.0.2–10.0.0.6|10.0.0.1|
|PC2|LAN2|20.0.0.2–20.0.0.6|20.0.0.1|
|PC3|LAN2|20.0.0.2–20.0.0.6|20.0.0.1|

---

## 🖥️ Server Setup (Manual IP)

Go to **Server → Desktop → IP Configuration**

| Server  | IP       | Subnet Mask     | Default Gateway |
| ------- | -------- | --------------- | --------------- |
| Server0 | 60.0.0.2 | 255.255.255.248 | 60.0.0.1        |
| Server1 | 50.0.0.2 | 255.255.255.248 | 50.0.0.1        |

---

### NAT Verification Commands
show ip nat translations
show ip nat statistics

---

## Test Checklist

-  PC0 → Ping Server0 (60.0.0.2)
    
-  PC1 → Ping Server1 (50.0.0.2)
    
-  PC2 → Ping Server0 (60.0.0.2)
    
-  PC3 → Ping Server1 (50.0.0.2)
    
-  Check `show ip nat translations` on both routers