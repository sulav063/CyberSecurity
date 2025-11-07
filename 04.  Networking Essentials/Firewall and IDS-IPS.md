## Firewall

![[Firewall.png]]

### What is a Firewall?
A **firewall** is a network security device (hardware or software) that **monitors, filters, and controls** incoming and outgoing network traffic based on **predefined security rules**.

It acts as a **barrier between trusted internal networks and untrusted external networks** (like the internet). Also known as the **First-Line of Defense.

Firewall can be physical device or a software.

---

### Purpose of a Firewall
- Prevent **unauthorized access** to or from a private network.
- Control **which services and ports** are allowed or blocked.
- Detect and stop **malicious activity**.

---

### Types of Firewalls
![[Types of Firewall.png]]

| Type                    | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| **Packet-Filtering Firewall** | Filters packets based on IP, port, and protocol. Operates at Layer 3/4. |
| **Stateful Firewall**         | Tracks active connections. Only allows return traffic from trusted sessions. |
| **Application Layer Firewall** | Analyzes traffic at Layer 7 (e.g., HTTP, FTP). Protects against specific app threats. |
| **Next-Generation Firewall (NGFW)** | Combines traditional firewall features with advanced ones like intrusion prevention (IPS), deep packet inspection (DPI), etc. |
| **Hardware Firewall**         | A dedicated appliance installed at the network perimeter. |
| **Software Firewall**         | Installed on individual computers (e.g., Windows Defender Firewall). |

---

## Firewall Rules

Firewall rules are sets of **conditions and actions** that determine whether to **allow**, **deny**, or **reject** network traffic.

###  Rule Actions

| Action  | Description                                                                 |
|---------|-----------------------------------------------------------------------------|
| **Allow**  | Permits the traffic to pass through the firewall.                         |
| **Deny**   | Silently blocks the traffic (no response is sent to the sender).          |
| **Reject** | Blocks the traffic and **sends an error response** (e.g., ICMP unreachable). |

###  Rule Conditions (Matching Criteria)

Each firewall rule is based on multiple **matching conditions** that define what kind of traffic is affected.

### 1. Source IP Address

- Defines **where the traffic is coming from**.
- Can be a single IP (e.g., `192.168.1.10`), a subnet (e.g., `192.168.1.0/24`), or `any`.

**Examples:**
- Allow traffic only from a specific device.
- Block an entire IP range or country.

### 2. **Destination IP Address**

- Defines **where the traffic is going**.
- Used to protect specific internal servers or services.

**Examples:**
- Block access to a specific server (`192.168.1.100`).
- Allow only internal systems to connect to the internet.

### 3. **Source Port**

- Identifies the port number **used by the sender’s device**.
- Often randomized, but sometimes fixed for specific services (e.g., DNS = 53).

### 4. **Destination Port**

- Identifies **which service the traffic is trying to reach**.
- Each service typically runs on a standard port:
  - HTTP → 80
  - HTTPS → 443
  - SSH → 22
  - FTP → 21

**Examples:**
- Deny all traffic to port 21 (FTP).
- Allow only HTTPS traffic (port 443).

### 5. **Protocol (TCP/UDP/ICMP)**

- Defines the **type of traffic**:
  - **TCP** – Reliable, connection-based (e.g., HTTP, SSH)
  - **UDP** – Unreliable, connectionless (e.g., DNS, video streaming)
  - **ICMP** – Used for diagnostics (e.g., ping)

**Examples:**
- Block all ICMP (to disable pinging).
- Allow only TCP connections on port 443.

### 6. **Direction (Inbound / Outbound) or Two Types of Traffics**

- **Inbound:** Traffic coming **into** your network or device.
- **Outbound:** Traffic going **out** to external destinations.

**Examples:**
- Allow inbound SSH only from specific IPs.
- Block outbound connections to social media domains.

### Firewall Rule Evaluation Order

1. **Rules are processed in order from top to bottom.**
2. First matching rule determines the action.
3. If no rules match, **default policy** applies (often "deny all").

###  Example Rule Table

| Rule # | Source IP      | Destination IP  | Port | Protocol | Direction | Action |
|--------|----------------|------------------|------|----------|-----------|--------|
| 1      | 192.168.1.5     | Any              | 22   | TCP      | Inbound   | Allow  |
| 2      | Any             | 192.168.1.10     | 80   | TCP      | Outbound  | Deny   |
| 3      | 10.0.0.0/8      | Any              | Any  | ICMP     | Inbound   | Reject |

---

## Workflow of a Firewall

A firewall follows a structured process to **inspect, filter, and control** network traffic based on defined rules and policies.

### 1. Packet Arrival

- A network packet **enters the firewall** (inbound or outbound).
- The packet contains:
  - Source IP
  - Destination IP
  - Protocol (TCP/UDP)
  - Source and destination ports
  - Flags and payload

### 2. Rule Matching

- The firewall **checks its rule set** (access control list) from **top to bottom**.
- It compares the packet against **criteria**:
  - Source IP address
  - Destination IP address
  - Source port
  - Destination port
  - Protocol (TCP/UDP/ICMP)
  - Direction (inbound or outbound)
  - Application or user (in advanced firewalls)

### 3. Decision (Allow / Deny / Reject)

- Once a matching rule is found:
  - **Allow**: Packet is forwarded to its destination.
  - **Deny**: Packet is silently dropped (no notification sent).
  - **Reject**: Packet is dropped and sender is notified (usually with an ICMP error).

> Note: If **no rules match**, the default policy is applied (often "deny all").

### 4. Logging (Optional)

- If logging is enabled, details about the packet (IP, port, time, action) are **recorded**.
- Useful for:
  - Security monitoring
  - Troubleshooting
  - Auditing
### 5. Stateful Inspection (If Enabled)

- For **stateful firewalls**, the session is **tracked**:
  - New, established, or related sessions are allowed.
  - Invalid or unsolicited sessions are blocked.
### 6. Packet Forwarding or Dropping

- After decision and inspection, the firewall either:
  - **Forwards** the packet to its destination (if allowed).
  - **Drops** the packet (if denied or invalid).
## Flow Summary
[Incoming Packet]
        ↓
[Match Ruleset]
        ↓
[Allow / Deny / Reject]
        ↓
[Log Event (Optional)]
        ↓
[State Tracking (If Stateful)]
        ↓
[Packet Forwarded or Dropped]

---

### Firewalls in Cybersecurity

- Prevent **external attacks** (e.g., DDoS, brute-force).
- Stop **data exfiltration** or unauthorized internal access.
- Used in **network segmentation** and **zero-trust architecture**.

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





