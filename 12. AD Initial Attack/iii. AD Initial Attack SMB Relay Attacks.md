# SMB Relay Attacks

## Overview

An **SMB Relay Attack** is a network attack in which an attacker intercepts an authentication request from a victim and relays it to another machine on the network. The attacker does not need to know or crack the victim's password. Instead, the attack abuses the authentication process itself.

This attack primarily targets environments using **NTLM (NT LAN Manager)** authentication, especially when **SMB Signing** is not enforced.

SMB Relay attacks are common during **Active Directory security assessments** because many organizations still have legacy configurations that allow NTLM authentication.

---

## What is SMB?

**Server Message Block (SMB)** is a network protocol developed by Microsoft for sharing files, printers, and other resources over a network.

SMB allows computers to:

- Share files
- Share printers
- Access remote folders
- Execute administrative tasks
- Communicate with Windows servers

SMB commonly operates on:

| Protocol | Port |
|----------|------|
| TCP | 445 |
| TCP | 139 (Legacy NetBIOS SMB) |

---

## What is NTLM?

**NTLM (NT LAN Manager)** is Microsoft's legacy authentication protocol.

Instead of sending passwords directly over the network, NTLM uses a **challenge-response** authentication mechanism.

Basic process:

```text
Client
   │
   ▼
Authentication Request
   │
   ▼
Server sends Challenge
   │
   ▼
Client calculates Response
   │
   ▼
Server verifies Response
```

Although more secure than sending plaintext passwords, NTLM has weaknesses that can be abused if modern protections are not enabled.

---

## How SMB Relay Works (Conceptually)

The following diagram shows the general authentication flow:

```text
Victim Computer
        │
        │ Authentication
        ▼
Attacker System
        │
        │ Relays Authentication
        ▼
Target SMB Server
        │
        ▼
Authentication Process
```

If protections such as SMB Signing are not enabled, the target server may accept the relayed authentication.

---

## Conditions Required

An SMB Relay attack generally requires:

- NTLM authentication enabled
- SMB Signing disabled or not enforced
- Network connectivity between systems
- A system attempting SMB authentication

Modern Windows environments with SMB Signing enforced are significantly more resistant to this type of attack.

---

## Potential Impact

If successful, an attacker may gain access to:

- Shared folders
- Network resources
- Administrative shares
- User data

Depending on the permissions of the authenticated user, this could result in unauthorized access to sensitive resources.

---

## SMB Signing

### What is SMB Signing?

SMB Signing digitally signs SMB packets to ensure their integrity and authenticity.

Benefits include:

- Preventing packet tampering
- Preventing relay of SMB traffic
- Verifying the identity of communicating systems

Enabling SMB Signing is one of the most effective defenses against SMB Relay attacks.

---

## Safe Enumeration Commands

### Check SMB Port

```bash
nmap -p 445 192.168.1.10
```

Checks whether the SMB service is available on the target.

---

### Identify SMB Protocol Versions

```bash
nmap --script smb-protocols -p445 192.168.1.10
```

Displays supported SMB protocol versions.

---

### Check SMB Security Configuration

```bash
nmap --script smb2-security-mode -p445 192.168.1.10
```

Shows whether SMB Signing is required or optional.

---

### View Available SMB Shares

```bash
smbclient -L //192.168.1.10
```

Lists shared resources that the server advertises.

---

### Display Network Interfaces

```bash
ip addr
```

Shows the available network interfaces.

---

### Display Routing Table

```bash
ip route
```

Displays routing information for the system.

---

### Check Active Network Connections

```bash
ss -tuln
```

Lists listening TCP and UDP ports.

---

### Display ARP Cache

```bash
arp -a
```

Shows devices that have recently communicated on the local network.

---

## Windows Commands

Display IP configuration:

```powershell
ipconfig /all
```

---

View network connections:

```powershell
netstat -ano
```

---

Display shared folders:

```powershell
net share
```

---

View mapped network drives:

```powershell
net use
```

---

Check the computer name:

```powershell
hostname
```

---

## Detection

Administrators should monitor for:

- Unusual NTLM authentication events
- Unexpected SMB authentication attempts
- Connections to unknown systems
- Repeated authentication failures
- Suspicious access to administrative shares

Useful monitoring tools include:

- Windows Event Viewer
- Microsoft Defender for Endpoint
- Sysmon
- SIEM platforms
- Network Intrusion Detection Systems (IDS)

---

## Prevention

Organizations should implement the following controls:

- Enable SMB Signing.
- Prefer Kerberos authentication over NTLM where possible.
- Disable unnecessary SMB services.
- Restrict NTLM usage.
- Keep Windows systems updated.
- Monitor SMB traffic.
- Apply the principle of least privilege.
- Segment internal networks to reduce lateral movement.

---

## Importance in Cybersecurity

SMB Relay attacks highlight the importance of secure authentication mechanisms in enterprise environments.

Understanding the conditions that make these attacks possible helps defenders:

- Audit Windows configurations
- Enforce SMB Signing
- Reduce reliance on NTLM
- Improve Active Directory security posture

---

## Interview Questions

### What is SMB?

SMB is a Microsoft protocol used for file and printer sharing over a network.

---

### What is NTLM?

NTLM is a legacy Microsoft authentication protocol based on challenge-response authentication.

---

### Why is SMB Signing important?

SMB Signing protects SMB communications from tampering and helps prevent relay attacks.

---

### Which port does SMB commonly use?

TCP Port **445**

---
