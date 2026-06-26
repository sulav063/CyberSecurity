# Introduction to LLMNR

## Overview

**Link-Local Multicast Name Resolution (LLMNR)** is a Microsoft protocol used for resolving hostnames on a local network when a DNS server cannot resolve a requested hostname.

It was introduced as a fallback mechanism to improve name resolution in small or disconnected networks. If a Windows machine cannot find a hostname through DNS, it sends a multicast request to other devices on the local network asking if anyone knows the IP address associated with that hostname.

LLMNR operates only on the local network segment and is enabled by default on many Windows operating systems.

---

## Why LLMNR Exists

Before LLMNR, systems relied primarily on DNS for hostname resolution. However, there are situations where DNS may fail:

- The DNS server is unavailable.
- The hostname is not registered in DNS.
- The hostname was misspelled.
- Small networks may not have a DNS server.

In these situations, LLMNR allows devices to communicate without requiring a centralized DNS server.

---

## How LLMNR Works

The hostname resolution process follows this order:

```text
Application
      │
      ▼
DNS Lookup
      │
      ▼
Found?
 ├── Yes → Return IP Address
 └── No
        │
        ▼
   LLMNR Broadcast
        │
        ▼
Local Devices Respond
        │
        ▼
Connection Established
```

---

## LLMNR Communication

LLMNR uses:

| Protocol | Port |
|----------|------|
| UDP | 5355 |

Unlike DNS, LLMNR uses **multicast communication** instead of querying a centralized DNS server.

---

## Example Scenario

Suppose a user tries to access:

```text
\\fileserver
```

Windows performs the following steps:

1. Query the configured DNS server.
2. DNS server cannot resolve the hostname.
3. Windows broadcasts an LLMNR request.
4. Any computer on the local network may respond.
5. Windows connects to the first valid response.

---

## Advantages

- Easy hostname resolution.
- No DNS server required.
- Useful in small LAN environments.
- Automatic fallback mechanism.

---

## Disadvantages

Because **LLMNR responses are not authenticated**, attackers may impersonate legitimate systems.

Possible risks include:

- Credential theft
- NTLM hash capture
- Man-in-the-Middle attacks
- SMB Relay attacks

---

## LLMNR vs DNS

| Feature | DNS | LLMNR |
|----------|-----|--------|
| Scope | Network/Internet | Local Network |
| Transport | UDP/TCP | UDP |
| Port | 53 | 5355 |
| Authentication | Yes | No |
| Security | Higher | Lower |

---

## Safe Verification Commands

### Display Network Interfaces

```bash
ip addr
```

Displays all available network interfaces.

---

### Display Routing Table

```bash
ip route
```

Shows the routing table.

---

### Display Hostname

```bash
hostname
```

Shows the current system hostname.

---

### Verify DNS Resolution

```bash
nslookup google.com
```

Queries a DNS server for hostname resolution.

---

### Test Name Resolution

```bash
ping localhost
```

Verifies local hostname resolution.

---

### View Listening UDP Ports

```bash
ss -ulpn
```

Lists UDP services currently listening on the system.

---

### Display Active Network Connections

```bash
netstat -anu
```

Displays active UDP connections.

---

### Display DNS Configuration

```bash
cat /etc/resolv.conf
```

Shows configured DNS servers on Linux.

---

## Windows Commands

Display computer name:

```powershell
hostname
```

Display IP configuration:

```powershell
ipconfig /all
```

Flush DNS cache:

```powershell
ipconfig /flushdns
```

Display DNS cache:

```powershell
ipconfig /displaydns
```

Test DNS resolution:

```powershell
nslookup example.com
```

---

## Detection

System administrators should monitor:

- Unexpected multicast traffic
- Excessive hostname broadcasts
- Authentication requests to unknown systems
- Unusual DNS failures

Monitoring tools include:

- Windows Event Viewer
- Wireshark
- Microsoft Defender
- SIEM solutions

---

## Prevention

Organizations should:

- Disable LLMNR if not required.
- Disable NetBIOS Name Service (NBT-NS).
- Use secure DNS infrastructure.
- Enable SMB Signing.
- Monitor multicast traffic.
- Enforce strong password policies.
- Keep systems updated.

---

## Real-World Importance

Many enterprise Windows environments still have LLMNR enabled.

Because of this, security professionals routinely check whether LLMNR is active during:

- Active Directory Security Assessments
- Internal Penetration Tests
- Red Team Exercises
- Security Audits

Understanding LLMNR helps defenders identify weaknesses and implement appropriate security controls.

---
