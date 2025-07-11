
---

## What Are Ports?

- A **port** is a logical connection point on a computer used to identify specific services or processes.
- Ports help determine **which application or service** should handle incoming or outgoing traffic.
- Each IP address supports **65,536 ports**:
  - **0–1023**: Well-known ports (assigned to standard protocols)
  - **1024–49151**: Registered ports (used by software apps)
  - **49152–65535**: Dynamic/private ports (temporary, client-side)

---

## What Are Protocols?

- A **protocol** is a set of rules that governs communication between network devices.
- Protocols define:
  - **Data formatting**
  - **Transmission methods**
  - **Error detection**
  - **Session handling**

---

## TCP vs UDP (Transport Protocols)

| Feature               | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol)         |
|-----------------------|-------------------------------------|--------------------------------------|
| Connection Type       | Connection-oriented                 | Connectionless                       |
| Reliability           | Reliable (ensures delivery)         | Unreliable (no delivery guarantee)   |
| Ordering              | Maintains order of packets          | No ordering of packets               |
| Error Checking        | Yes (with acknowledgment)           | Yes (basic checksum only)            |
| Speed                 | Slower (due to overhead)            | Faster (less overhead)               |
| Use Cases             | Web (HTTPS), email, file transfer   | DNS, video streaming, VoIP, games    |
| Header Size           | 20–60 bytes                         | 8 bytes                              |
| Congestion Control    | Yes                                 | No                                   |

> TCP is used when **accuracy** is critical.  
> UDP is used when **speed** is more important than reliability.

---

## Common Ports and Their Protocols

| Port  | Protocol           | Description                                      | Transport | Layer (TCP/IP Model) |
|-------|--------------------|--------------------------------------------------|-----------|----------------------|
| 20    | FTP (Data)         | File Transfer Protocol – data channel            | TCP       | Application          |
| 21    | FTP (Control)      | File Transfer Protocol – command control         | TCP       | Application          |
| 22    | SSH                | Secure Shell – Encrypted remote access           | TCP       | Application          |
| 23    | Telnet             | Unsecured remote terminal access                 | TCP       | Application          |
| 25    | SMTP               | Simple Mail Transfer Protocol (email sending)    | TCP       | Application          |
| 53    | DNS                | Domain Name System – hostname to IP resolution   | TCP/UDP   | Application          |
| 67    | DHCP (Server)      | Dynamic Host Configuration Protocol – server     | UDP       | Application          |
| 68    | DHCP (Client)      | Dynamic Host Configuration Protocol – client     | UDP       | Application          |
| 69    | TFTP               | Trivial File Transfer Protocol – basic file transfer | UDP    | Application          |
| 80    | HTTP               | HyperText Transfer Protocol – unencrypted web    | TCP       | Application          |
| 110   | POP3               | Post Office Protocol v3 – basic email retrieval  | TCP       | Application          |
| 123   | NTP                | Network Time Protocol – clock synchronization    | UDP       | Application          |
| 143   | IMAP               | Internet Message Access Protocol – email sync    | TCP       | Application          |
| 161   | SNMP               | Simple Network Management Protocol               | UDP       | Application          |
| 443   | HTTPS              | HTTP Secure – encrypted web traffic (SSL/TLS)    | TCP       | Application          |
| 445   | SMB                | Server Message Block – Windows file sharing      | TCP       | Application          |
| 389   | LDAP               | Lightweight Directory Access Protocol            | TCP/UDP   | Application          |
| 636   | LDAPS              | LDAP over SSL/TLS – secure directory access      | TCP       | Application          |
| 3306  | MySQL              | MySQL Database access                            | TCP       | Application          |
| 990   | FTPS               | FTP Secure – FTP over SSL                        | TCP       | Application          |
| 3389  | RDP                | Remote Desktop Protocol – remote Windows access  | TCP       | Application          |

---

# Port Number Ranges in Networking

Each IP address supports **65,536 ports** for communication, used to identify services and applications running on a device.

---

## Port Range Breakdown

| Port Range             | Port Numbers       | Description                                                  |
|------------------------|--------------------|--------------------------------------------------------------|
| **Well-known ports**   | 0 – 1023           | Reserved for core services and protocols (e.g., HTTP, FTP, SSH) |
| **Registered ports**   | 1024 – 49151       | Assigned to software applications by IANA                     |
| **Dynamic/Private ports** | 49152 – 65535    | Temporary ports for client-side communication (ephemeral)    |

---

## Example Use Cases

| Port | Protocol | Use Case                      |
|------|----------|-------------------------------|
| 80   | HTTP     | Web browsing (unencrypted)    |
| 443  | HTTPS    | Secure web access             |
| 22   | SSH      | Secure remote terminal access |
| 53   | DNS      | Name resolution               |
| 3389 | RDP      | Remote Desktop on Windows     |

---

## TCP/IP Model Mapping

| Layer            | Function                          | Protocol Examples                          |
|------------------|-----------------------------------|---------------------------------------------|
| Application      | Interface for user and services   | HTTP, FTP, SSH, DNS, SMTP                   |
| Transport        | End-to-end communication          | TCP, UDP                                    |
| Internet         | Routing and addressing             | IP, ICMP, ARP                               |
| Network Access   | Physical transmission             | Ethernet, MAC, Wi-Fi, DSL                   |

> Ports operate at the **Transport Layer**, helping direct traffic to the correct application via **TCP or UDP**.

---

## Cybersecurity Relevance

- **Port Scanning**: Use tools like `nmap`, `masscan` to scan for **open ports**.
- **Enumeration**: Identify services on open ports using **banner grabbing**.
- **Vulnerability Identification**:
  - Port **21 (FTP)** → Common for brute force or misconfigured file sharing
  - Port **23 (Telnet)** → Transmits credentials in plaintext
  - Port **445 (SMB)** → Often targeted in Windows exploits (e.g., EternalBlue)
- **Defense**:
  - Disable or block unused ports via firewall
  - Monitor traffic with IDS/IPS tools
  - Enforce encryption (e.g., HTTPS, SFTP)

---

