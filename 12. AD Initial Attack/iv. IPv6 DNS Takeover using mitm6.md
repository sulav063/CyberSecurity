
## Overview

IPv6 DNS Takeover is an attack technique that takes advantage of Windows systems preferring IPv6 over IPv4 in certain network configurations. If IPv6 is enabled but not properly managed, a malicious device on the local network may influence how systems discover DNS servers and other network services.

The tool **mitm6** is commonly discussed in cybersecurity education as an example of software that demonstrates how insecure IPv6 configurations can be abused in a lab environment.

---

## Why IPv6 Is Important

IPv6 is the successor to IPv4 and provides a much larger address space. Modern Windows operating systems enable IPv6 by default, and many enterprise networks support it even if it is not actively used.

---

## Concept

When a Windows computer joins a network, it attempts to discover network configuration automatically. If IPv6 configuration is accepted without proper security controls, the system may communicate using unintended network settings.

This demonstrates why proper IPv6 configuration and monitoring are important in enterprise environments.

---

## Potential Risks

Improper IPv6 configuration may contribute to:

- Incorrect DNS resolution
    
- Authentication exposure
    
- Network traffic redirection
    
- Increased attack surface
    

---

## Detection

Administrators should regularly monitor:

- IPv6-enabled interfaces
    
- DNS configuration
    
- Unexpected IPv6 routers
    
- Network discovery traffic
    

---

## Prevention

Organizations can improve security by:

- Disabling IPv6 if it is not required.
    
- Monitoring IPv6 traffic.
    
- Using secure DNS infrastructure.
    
- Enforcing SMB Signing.
    
- Applying security updates.
    
- Segmenting internal networks.
    

---

## Importance in Cybersecurity

Understanding IPv6 helps security professionals identify configuration weaknesses and strengthen enterprise network security.

---

# Basic IPv6 Commands

These commands are useful for viewing and verifying IPv6 network configurations. They are commonly used by network administrators and cybersecurity professionals to inspect IPv6 settings and troubleshoot connectivity issues.

---

## Display IPv4 and IPv6 Addresses

```bash
ip addr
```

Displays all available network interfaces along with their assigned IPv4 and IPv6 addresses.

---

## Display Only IPv6 Addresses

```bash
ip -6 addr
```

Shows only the IPv6 addresses configured on the system, making it easier to inspect IPv6-specific settings.

---

## Display IPv6 Routing Table

```bash
ip -6 route
```

Displays the IPv6 routing table, including routes used to reach IPv6 networks and gateways.

---

## Test IPv6 Connectivity

```bash
ping6 ::1
```

Tests IPv6 connectivity by sending ICMPv6 echo requests to the IPv6 loopback address (`::1`). This is useful for verifying that the IPv6 networking stack is functioning correctly.

---

## Show IPv6 Neighbor Table

```bash
ip -6 neigh
```

Displays the IPv6 Neighbor Discovery table, which contains information about nearby IPv6 devices that have recently communicated with the system.

---

## Display Network Interfaces

```bash
ip link show
```

Lists all available network interfaces along with their current status (UP or DOWN), MAC addresses, and interface details.

---

## Display Current Hostname

```bash
hostname
```

Displays the hostname of the current system.

---

# Windows IPv6 Commands

The following commands can be used in **Command Prompt (CMD)** or **PowerShell** on Windows systems.

---

## Display IP Configuration

```bash
ipconfig /all
```

Displays detailed network configuration, including IPv4 addresses, IPv6 addresses, DNS servers, gateways, and adapter information.

---

## Display IPv6 Routing Table

```bash
netsh interface ipv6 show route
```

Displays all IPv6 routes currently configured on the Windows system.

---

## Display IPv6 Interfaces

```bash
netsh interface ipv6 show interface
```

Lists all IPv6-enabled network interfaces, including interface indexes and operational status.

---
