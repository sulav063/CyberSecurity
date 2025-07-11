## VPN (Virtual Private Network)

### What is a VPN?

A **VPN** creates a secure, encrypted tunnel over the internet between your device and a remote network or server.

It hides your IP address and encrypts all your internet traffic, making it **secure and private**.

---

### Purpose of VPN

- Protect data on **public networks** (e.g., Wi-Fi in cafes).
- Enable **secure remote access** to private corporate networks.
- Bypass **geo-restrictions** or censorship.
- Mask IP address and user location.

---

### How VPN Works

1. The user connects to a VPN **client**.
2. The VPN client establishes a **secure tunnel** to a **VPN server**.
3. All data is **encrypted** and routed through the VPN server.
4. The server decrypts and forwards data to the final destination.

---

### VPN Protocols

| Protocol      | Description                                      |
|---------------|--------------------------------------------------|
| **PPTP**      | Fast but outdated and insecure.                  |
| **L2TP/IPsec**| Adds encryption to L2TP using IPsec.             |
| **OpenVPN**   | Open-source, strong encryption, widely used.     |
| **IKEv2/IPsec**| Good for mobile devices, fast reconnections.    |
| **WireGuard** | Modern, fast, lightweight protocol.              |

---

### Types of VPN

| Type             | Use Case                                        |
|------------------|--------------------------------------------------|
| **Remote Access VPN** | Secure connection for users to access internal networks remotely. |
| **Site-to-Site VPN**  | Connects two entire networks (e.g., branch offices). |
| **Client-to-Site VPN**| Used by employees to securely access their organization’s network from outside. |

---

### VPN in Cybersecurity

- **Encrypts data** in transit, protecting against eavesdropping and MITM attacks.
- Helps implement **secure remote work**.
- Often combined with **MFA** and **firewall rules** for extra security.
---
## IDS and IPS

IDS (Intrusion Detection System) and IPS (Intrusion Prevention System) are network security tools designed to **monitor**, **detect**, and in the case of IPS, **block** malicious traffic and behavior.

---

### What is IDS (Intrusion Detection System)?

An **IDS** is a monitoring system that **analyzes network or system traffic** for suspicious activity and known attack patterns.

### Function:
- **Detects threats** and anomalies.
- **Generates alerts** when malicious activity is found.
- Does **not block** traffic — it is a **passive system**.

### Use Cases:
- Security logging and monitoring.
- Forensic analysis and incident response.
- Detecting attacks like port scanning, buffer overflows, malware signatures.

---

### What is IPS (Intrusion Prevention System)?

An **IPS** is like an IDS but **actively blocks or prevents** detected malicious traffic in real-time.

### Function:
- **Detects** and **prevents** attacks automatically.
- Sits **inline** with network traffic (between source and destination).
- Can **drop packets, reset connections, or quarantine** systems.

### Use Cases:
- Blocking brute force or DoS attacks.
- Real-time protection of web servers, databases, and endpoints.
- Enforcing security policies automatically.

---

## Difference Between Firewall, IDS, and IPS

![[FW vs IDS vs IPS.png]]

| Feature              | **Firewall**                                | **IDS (Intrusion Detection System)**         | **IPS (Intrusion Prevention System)**         |
|----------------------|----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| Primary Function      | Filters traffic based on predefined rules   | Monitors and alerts on suspicious activity    | Detects and actively blocks threats           |
| Placement             | Network perimeter (entry/exit points)       | Out-of-band (passive monitoring)              | Inline with traffic (active filtering)        |
| Action                | Allow, deny, or reject packets              | Sends alerts/logs; takes no automatic action  | Blocks or drops malicious packets             |
| Traffic Impact        | Directs traffic based on rules              | No impact on traffic flow                     | Can affect traffic latency/blocking           |
| Focus                 | IP, port, protocol-level filtering          | Behavioral or signature-based threat detection| Signature and anomaly-based prevention        |
| Can Stop Attacks?     | Only known/defined traffic rules            | No – only detects and reports                 | Yes – detects and blocks in real time         |
| Logging               | Optional (basic logging)                    | Detailed logging and alerting                 | Logging with active prevention                |
| False Positives       | Low (rules are strict)                      | Possible, requires analysis                   | Possible – may block legitimate traffic       |
| Example Use Case      | Block all external FTP access               | Alert on brute-force login attempts           | Block DDoS or malware-based attack            |
| Examples              | pfSense, Cisco ASA, iptables                | Snort, Zeek (Bro), OSSEC                      | Snort (inline mode), Suricata, Cisco IPS      |

---

## Types of IDS/IPS

| Type           | Description                                       |
|----------------|---------------------------------------------------|
| **Network-based (NIDS/NIPS)** | Monitors network traffic for suspicious patterns. Placed at strategic points in the network. |
| **Host-based (HIDS/HIPS)**   | Monitors a specific host (e.g., server or endpoint) by analyzing OS logs, system calls, etc. |

---

## Detection Methods

| Method             | Description                                                |
|--------------------|------------------------------------------------------------|
| **Signature-Based** | Detects known attacks by matching patterns or "signatures". |
| **Anomaly-Based**   | Uses baselines to detect deviations in normal behavior.     |
| **Heuristic-Based** | Uses rules and algorithms to detect suspicious behavior.    |

---

## IDS/IPS Deployment Example

- **Firewall** filters based on rules (IP, port, protocol).
- **IDS** monitors traffic and alerts about threats (e.g., port scan).
- **IPS** blocks malicious packets (e.g., SQL injection attempt).

---

## Tools & Technologies

| Tool         | Type        | Description                          |
|--------------|-------------|--------------------------------------|
| **Snort**    | IDS/IPS     | Open-source, signature-based system. |
| **Suricata** | IDS/IPS     | Multi-threaded IDS/IPS engine.       |
| **Zeek (Bro)**| IDS        | Anomaly-based network monitoring.    |
| **OSSEC**    | HIDS        | Host-based intrusion detection.      |

