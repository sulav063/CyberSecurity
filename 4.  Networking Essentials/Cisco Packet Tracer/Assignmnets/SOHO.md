# 🌐 SOHO Network Design for Company

This design outlines a SOHO network connecting 2 PCs, 2 laptops, and 1 VoIP phone to a server via two routers with static routing. The network uses a wireless router (WPC300N) for DHCP and internal connectivity, with corrected DHCP and Internet settings.

---

### Network Overview

- **Router0**: Main router handling internal LAN and connection to Router1.
- **Router1**: Connects to Router0 and the company server.
- **Wireless Router (WPC300N)**: Manages DHCP for 2 PCs, 2 laptops, and 1 VoIP phone.
- **Devices**: 2 PCs, 2 laptops, 1 VoIP phone, and a server.
- **Connections**: Static routing between Router0 and Router1, DHCP for internal devices.
![[SOHO.png]]
---

### Router0 Configuration

```bash
enable
configure terminal

# Interface to internal LAN (via WPC300N)
interface gigabitEthernet0/1
ip address 192.168.0.1 255.255.255.0
no shutdown
exit

# Interface to Router1
interface gigabitEthernet0/0
ip address 172.16.1.1 255.255.255.252
no shutdown
exit

# Static route to Server network through Router1
ip route 10.0.0.0 255.255.255.252 172.16.1.2
exit
```

---

### Router1 Configuration

```bash
enable
configure terminal

# Interface facing Router0
interface gigabitEthernet0/0
ip address 172.16.1.2 255.255.255.252
no shutdown
exit

# Interface facing Server
interface gigabitEthernet0/1
ip address 10.0.0.1 255.255.255.252
no shutdown
exit

# Static route to Router0's internal network
ip route 192.168.0.0 255.255.255.0 172.16.1.1
exit
```

---

### Server Configuration

- **Desktop > IP Configuration**
    - IP Address: `10.0.0.2`
    - Subnet Mask: `255.255.255.252`
    - Default Gateway: `10.0.0.1`

---

### Wireless Router (WPC300N) Configuration

- **Internet Setup**
    
    - Connection Type: Static IP
    - Internet IP Address: 203.0.113.1
    - Subnet Mask: 255.255.255.0
    - Default Gateway: 203.0.113.1
    - DNS 1: 8.8.8.8
    - DNS 2: 8.8.4.4
- **Network Setup**
    
    - Router IP Address: 192.168.0.1
    - Subnet Mask: 255.255.255.0
    - DHCP Server: Enabled
    - Start IP Address: 192.168.0.100
    - Maximum Number of Users: 50
    - IP Address Range: 192.168.0.100 - 192.168.0.149
    - Client Lease Time: 0 (one day)
    - Static DNS 1: 8.8.8.8
    - Static DNS 2: 8.8.4.4
    - WINS: 0.0.0.0
    - ISP VLANs: Disabled

---

### Device Configuration (2 PCs, 2 Laptops, 1 VoIP)

- **Steps**:
    1. Connect to WPC300N wirelessly or via Ethernet.
    2. Go to **Desktop > IP Configuration**.
    3. Select **DHCP**.
    4. IPs will auto-assign from `192.168.0.100 - 192.168.0.149`.

---

### Wiring Connections

- **Laptop1** → **Wireless Router (WPC300N)**: Ethernet cable from Laptop1's network port to a LAN port on WPC300N (or wireless connection).
- **Laptop2** → **Wireless Router (WPC300N)**: Ethernet cable from Laptop2's network port to a LAN port on WPC300N (or wireless connection).
- **PC1** → **Wireless Router (WPC300N)**: Ethernet cable from PC1's network port to a LAN port on WPC300N.
- **PC2** → **Wireless Router (WPC300N)**: Ethernet cable from PC2's network port to a LAN port on WPC300N.
- **Home-VoIP-PT** → **Wireless Router (WPC300N)**: Ethernet cable from VoIP phone's network port to a LAN port on WPC300N.
- **Wireless Router (WPC300N)** → **Router0 (Gig0/1)**: Ethernet cable from WPC300N's WAN port to Router0's Gig0/1 port.
- **Router0 (Gig0/0)** → **Router1 (Gig0/0)**: Ethernet cable between Router0's Gig0/0 port and Router1's Gig0/0 port.
- **Router1 (Gig0/1)** → **Server (Fa0)**: Ethernet cable from Router1's Gig0/1 port to Server's Fa0 port.

---

### Verification Steps

#### 1. Check Interface Status

```bash
show ip interface brief
```

- Expected: Router0 G0/0, G0/1 and Router1 G0/0, G0/1: `up up`

#### 2. Ping Tests

- From PC1 → Server: `ping 10.0.0.2`
- From Server → PC1: `ping 192.168.0.x` (replace x with assigned IP)
- From Router0 → Router1: `ping 172.16.1.2`
- From Router1 → Router0: `ping 172.16.1.1`

---

### IP Address Summary

| Device       | Interface         | IP Address  | Subnet Mask     | Notes                      |
| ------------ | ----------------- | ----------- | --------------- | -------------------------- |
| Router0      | G0/0 (to Router1) | 172.16.1.1  | 255.255.255.252 | WAN link to Router1        |
| Router0      | G0/1 (to WPC300N) | 192.168.0.1 | 255.255.255.0   | Internal LAN               |
| Router1      | G0/0 (to Router0) | 172.16.1.2  | 255.255.255.252 | WAN link to Router0        |
| Router1      | G0/1 (to Server)  | 10.0.0.1    | 255.255.255.252 | Server LAN                 |
| Server       | —                 | 10.0.0.2    | 255.255.255.252 | Static IP                  |
| Laptop1/2    | via DHCP          | 192.168.0.x | 255.255.255.0   | Assigned by WPC300N (DHCP) |
| PC1/2        | via DHCP          | 192.168.0.x | 255.255.255.0   | Assigned by WPC300N (DHCP) |
| Home-VoIP-PT | via DHCP          | 192.168.0.x | 255.255.255.0   | Assigned by WPC300N (DHCP) |