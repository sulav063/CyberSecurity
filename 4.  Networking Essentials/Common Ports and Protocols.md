
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

| Port | Protocol           | Description                                | Transport | Layer (TCP/IP Model) |
|------|--------------------|--------------------------------------------|-----------|----------------------|
| 20   | FTP (Data)         | File transfer (data channel)               | TCP       | Application          |
| 21   | FTP (Control)      | File transfer (commands)                   | TCP       | Application          |
| 22   | SSH                | Secure shell for remote login              | TCP       | Application          |
| 23   | Telnet             | Unsecured remote access                    | TCP       | Application          |
| 25   | SMTP               | Email sending                              | TCP       | Application          |
| 53   | DNS                | Domain name resolution                     | TCP/UDP   | Application          |
| 67   | DHCP (Server)      | IP assignment from server                  | UDP       | Application          |
| 68   | DHCP (Client)      | IP assignment to client                    | UDP       | Application          |
| 69   | TFTP               | Simple file transfer (no authentication)   | UDP       | Application          |
| 80   | HTTP               | Unsecure web access                        | TCP       | Application          |
| 110  | POP3               | Basic email retrieval                      | TCP       | Application          |
| 123  | NTP                | Time synchronization                       | UDP       | Application          |
| 137–139 | NetBIOS         | Legacy Windows file sharing                | TCP/UDP   | Application          |
| 143  | IMAP               | Advanced email sync                        | TCP       | Application          |
| 161  | SNMP               | Network monitoring and management          | UDP       | Application          |
| 443  | HTTPS              | Secure web access with SSL/TLS             | TCP       | Application          |
| 445  | SMB                | Windows file sharing and printer access    | TCP       | Application          |
| 3389 | RDP                | Remote desktop protocol                    | TCP       | Application          |

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
