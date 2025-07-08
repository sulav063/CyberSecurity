
---

## NAT (Network Address Translation)

### Definition  
**NAT** is a method used to translate **private IP addresses** within a local network to a **public IP address** for communication over the internet.

### Purpose  
- Conserves public IP addresses.  
- Allows multiple devices in a private network to access the internet using a single public IP.  
- Provides basic internal network security by hiding internal IP addresses.

## Types of NAT

# Types of NAT  
*Module 4 – Networking Essentials > Routing and Subnetting*

**Network Address Translation (NAT)** comes in different types, depending on how internal (private) IP addresses are mapped to external (public) IP addresses.

## 1. Static NAT

### Definition  
Maps **one private IP address** to **one public IP address**.

### Use Case  
Used when a device (e.g., internal web or mail server) must be **consistently accessible** from the outside world.

### Example  
- Private IP: `192.168.1.10`  
- Public IP: `49.45.200.50`  
- Mapping is always fixed.

### Pros  
- Simple to configure.  
- Useful for hosting services inside a private network.

### Cons  
- Requires one public IP for each private IP — **not scalable**.

## 2. Dynamic NAT

### Definition  
Maps **private IP addresses** to **a pool of public IP addresses** dynamically on a first-come, first-served basis.

### Use Case  
When a limited number of public IPs are shared among many private hosts that don't all need to access the internet at once.

### Example  
- Private IPs: `192.168.1.0/24`  
- Public IP Pool: `49.45.200.50 – 49.45.200.60`  
- Any 11 private devices can be translated at a time.

### Pros  
- Better IP conservation than Static NAT.  
- Automatically assigns available public IPs from a pool.

### Cons  
- If the pool is exhausted, **new connections are blocked**.  
- No consistent mapping — can cause issues for services expecting a fixed IP.

## 3. PAT (Port Address Translation) – Also Known as NAT Overload

### Definition  
Maps **many private IP addresses** to **a single public IP address**, using **different port numbers** to track sessions.

### Use Case  
Most commonly used in home, office, and enterprise networks for internet access.

### Example  
| Private IP         | Public IP and Port        |
|--------------------|---------------------------|
| 192.168.1.10:5000  | 49.45.200.50:30001         |
| 192.168.1.11:5001  | 49.45.200.50:30002         |

### Pros  
- Extremely **scalable**.  
- Conserves public IPs efficiently.  
- Most widely used form of NAT.

### Cons  
- Adds some complexity (port tracking).  
- May interfere with some protocols that embed IP or port info in data.

## Comparison Table

| Feature              | Static NAT                   | Dynamic NAT                    | PAT (NAT Overload)               |
|----------------------|------------------------------|--------------------------------|----------------------------------|
| Mapping Type         | One-to-One                   | Many-to-Many (from a pool)     | Many-to-One (with port tracking)|
| Public IPs Needed    | One per device               | Pool of public IPs             | One or few                       |
| Scalability          | Low                          | Medium                         | High                             |
| Used For             | Hosting internal services    | Temporary external access      | Internet access from LAN         |
| Consistency          | Always same public IP        | Varies                         | Varies (same IP, diff. ports)    |

---

## How NAT and PAT Work

1. Device with private IP (e.g., 192.168.0.5) sends a packet to the internet.
2. The router modifies the **source IP** (and **port** in PAT) to the **public IP**.
3. The destination server responds to the public IP.
4. The router translates it back to the original private IP and forwards it to the correct device.

---

## Private vs Public IP Addresses

### Private IP Address  
- Used **inside local networks** (e.g., home, school, office).  
- Cannot be routed on the internet directly.  
- Defined by the following ranges:

| IP Range                     | Default Subnet Mask     | CIDR Notation   |
|-----------------------------|--------------------------|-----------------|
| `10.0.0.0 – 10.255.255.255` | `255.0.0.0`              | `10.0.0.0/8`    |
| `172.16.0.0 – 172.31.255.255`| `255.240.0.0`            | `172.16.0.0/12` |
| `192.168.0.0 – 192.168.255.255` | `255.255.0.0` (varies) | `192.168.0.0/16`|

### Public IP Address  
- Used to **identify devices on the internet**.  
- Must be **unique and routable** globally.  
- Assigned by **ISPs or cloud providers**.

---

## Why NAT/PAT is Important

- IPv4 has limited public IPs — NAT helps preserve them.  
- Enhances security by **hiding internal network structure**.  
- Enables **multiple devices** to share **one internet-facing IP**.

---

## Summary Table

| Feature          | NAT                          | PAT                              |
|------------------|------------------------------|----------------------------------|
| Full Name        | Network Address Translation  | Port Address Translation         |
| Mapping          | IP-to-IP                     | IP and Port-to-IP and Port       |
| IP Usage         | May need multiple public IPs | Can work with just one public IP |
| Scalability      | Limited                      | High                             |
| Common Use Case  | Static IP mapping            | Home/Office internet sharing     |

