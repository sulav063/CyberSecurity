## VPN (Virtual Private Network)

### What is a VPN?

A **VPN** creates a secure, encrypted tunnel mechanism the internet between your device and a remote network or server.

It hides your IP address and encrypts all your internet traffic, making it **secure and private**.
![[VPN.png]]

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
## Types of VPN

VPNs can be classified based on how they connect users and networks. Below are the major types:
![[Pasted image 20250711185536.png]]

### 1. Remote Access VPN

- Allows **individual users** to securely connect to a private network from a remote location.
- Common in **work-from-home** or **mobile access** scenarios.
- Requires VPN client software (e.g., OpenVPN, Cisco AnyConnect).

**Use Case:** Employees accessing company files from home.

### 2. Site-to-Site VPN (Intranet-Based VPN)

- Connects **entire networks** (e.g., branch offices to headquarters).
- Typically configured between two routers or firewalls.
- Traffic between networks is encrypted and securely routed.

**Use Case:** Securely linking office branches over the internet.


### 3. Client-to-Site VPN (Hybrid of Remote Access & Site-to-Site)

- Allows an individual device to securely access a corporate network, similar to Remote Access VPN.
- Often includes more **authentication and security layers** than basic remote VPNs.

**Use Case:** Secure developer access to a cloud-based infrastructure.

### 4. Network-Based VPNs

These VPNs are deployed at the **network edge (e.g., gateway, firewall, or cloud platform)** and typically **do not require VPN clients** on end-user devices.

#### Types of Network-Based VPNs:

| Type                     | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **MPLS VPN (Layer 3 VPN)**    | Uses Multiprotocol Label Switching to create private, secure WAN links.         |
| **DMVPN (Dynamic Multipoint VPN)** | Cisco solution using GRE tunnels with IPsec for scalable mesh VPNs.          |
| **Cloud VPN (e.g., AWS, Azure)** | Creates secure tunnels between on-prem networks and cloud VPCs.               |
| **IPsec Tunnel VPN**     | Router-to-router VPN using IPsec; often used in site-to-site or B2B scenarios. |

**Use Case:** Large enterprises and ISPs securing traffic between data centers, branch offices, or cloud regions.

---
### VPN in Cybersecurity

- **Encrypts data** in transit, protecting against eavesdropping and MITM attacks.
- Helps implement **secure remote work**.
- Often combined with **MFA** and **firewall rules** for extra security.
---
## What is a Proxy?

A **proxy** (or proxy server) acts as an **intermediary between a client and the destination server**. When a user sends a request (like visiting a website), the request goes through the proxy first. The proxy then sends the request to the destination on behalf of the user.

---

### Purpose of a Proxy

- **Hide user IP address** (provides anonymity).
- **Bypass content restrictions** (geo-blocking or censorship).
- **Control internet usage** (e.g., in offices/schools).
- **Cache content** for faster access.
- **Filter or block traffic** based on policies.

---

### Types of Proxy Servers

| Type               | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| **Forward Proxy**  | Sits between the user and the internet. Used to filter, cache, or block traffic. |
| **Reverse Proxy**  | Sits in front of web servers to handle requests on their behalf. Provides load balancing and security. |
| **Transparent Proxy** | Intercepts traffic without user configuration. Often used by ISPs or organizations. |
| **Anonymous Proxy**   | Hides the user's IP but identifies itself as a proxy.                     |
| **High Anonymity Proxy** | Hides both IP and proxy usage completely.                         |
| **SOCKS Proxy**    | A general-purpose proxy that works at the transport layer (supports TCP/UDP). |
| **HTTP Proxy**     | Specifically handles HTTP and HTTPS traffic.                              |

---

## Difference Between VPN and Proxy

| Feature               | VPN (Virtual Private Network)                          | Proxy Server                                      |
|------------------------|--------------------------------------------------------|---------------------------------------------------|
| **Function**           | Encrypts and tunnels all traffic through a secure server | Forwards specific traffic (e.g., web) to a proxy server |
| **Encryption**         | Yes – Encrypts all data between client and server      | No (unless used with HTTPS)                       |
| **Traffic Coverage**   | All internet traffic (system-wide)                     | Application-specific (e.g., web browser only)     |
| **IP Masking**         | Yes – Replaces public IP with VPN server’s IP          | Yes – Replaces IP for specific requests           |
| **Security Level**     | High – Provides privacy and encryption                 | Low to medium – Provides anonymity, but limited security |
| **Speed Impact**       | Slight slowdown due to encryption                      | Typically faster (no encryption overhead)         |
| **Use Case**           | Secure communication, remote access, privacy           | Bypass content restrictions, web filtering        |
| **System Integration** | Requires system or router-level setup                  | Set up per app/browser (e.g., proxy settings)     |
| **Protocols Used**     | OpenVPN, IKEv2/IPsec, WireGuard, etc.                  | HTTP, HTTPS, SOCKS                                |
| **Example**            | NordVPN, Cisco AnyConnect, OpenVPN                     | Squid Proxy, CCProxy, Tor Browser (via proxy)     |

![[VPN Vs Proxy.png]]

---


