
---

## NAT (Network Address Translation)

### Definition  
**NAT** is a method used to translate **private IP addresses** within a local network to a **public IP address** for communication over the internet.

### Purpose  
- Conserves public IP addresses.  
- Allows multiple devices in a private network to access the internet using a single public IP.  
- Provides basic internal network security by hiding internal IP addresses.

## Types of NAT

| Type             | Description                                                              |
|------------------|---------------------------------------------------------------------------|
| **Static NAT**   | One-to-one mapping between private and public IPs. Used for servers.      |
| **Dynamic NAT**  | Maps private IPs to a pool of public IPs. Limited scalability.            |
| **PAT**          | Many-to-one mapping using port numbers. Most commonly used.               |

---

## PAT (Port Address Translation)

### Definition  
**PAT**, also known as **NAT Overload**, is a type of NAT that maps **multiple private IP addresses** to a **single public IP address** using different **port numbers**.

### Example  
- Three devices (192.168.1.10, 192.168.1.11, 192.168.1.12) access the internet via 1 public IP (e.g., 49.45.200.15).  
- PAT uses port numbers to track individual connections:
  - 192.168.1.10:1234 → 49.45.200.15:5001  
  - 192.168.1.11:1235 → 49.45.200.15:5002

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

