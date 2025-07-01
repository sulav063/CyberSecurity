
Routing and switching are core functions in networking that determine how data travels within and between networks.

---

## Switching

### Definition  
Switching is the process of forwarding data **within the same network (LAN)** based on MAC addresses.

### OSI Layer  
Operates at **Layer 2 – Data Link Layer**.

### How Switching Works  
- Switches connect devices like PCs, printers, and servers.  
- Each device is assigned a dedicated physical port.  
- The switch reads the **MAC address** from incoming data frames.  
- Builds and uses a **MAC address table** to track device-port associations.  
- Forwards data only to the destination port, reducing unnecessary traffic.

### Types of Switching  
- **Circuit Switching** – Used in traditional telephone networks.  
- **Packet Switching** – Most common in IP networks today.  
- **Message Switching** – Historical, rarely used.

### Benefits of Switching  
- Reduces network collisions.  
- Improves LAN performance through selective data forwarding.  
- Supports **VLANs** for segmentation and security.  
- Enables **full-duplex** communication.

---

## Routing

### Definition  
Routing is the process of directing data **between different networks** using IP addresses.

### OSI Layer  
Operates at **Layer 3 – Network Layer**.

### How Routing Works  
- Routers connect different networks (e.g., LAN to WAN/internet).  
- They inspect the **IP header** of each packet.  
- Use a **routing table** to determine the best next hop.  
- Forward packets toward their destination network.

### Types of Routing

| Type            | Description                                                  |
|-----------------|--------------------------------------------------------------|
| **Static**      | Manually configured routes. Simple, but not flexible.        |
| **Dynamic**     | Routes are updated automatically using routing protocols.    |

### Common Routing Protocols  
- **RIP** – Hop count-based; simple but limited.  
- **OSPF** – Link-state; efficient and faster.  
- **BGP** – Used between ISPs and large networks (internet backbone).

---

## DHCP (Dynamic Host Configuration Protocol)

### Definition  
DHCP is a network protocol used to **automatically assign IP addresses** and other configuration information to devices on a network.

### Function  
- Reduces the need for manual IP configuration.  
- Assigns IP address, subnet mask, default gateway, and DNS settings dynamically.  

### OSI Layer  
Primarily operates at **Layer 7 – Application Layer**, but influences Layer 3 operations.

### DHCP Components  
- **DHCP Server** – Assigns and manages IP addresses.  
- **DHCP Client** – Device requesting IP information.  
- **DHCP Lease** – Temporary IP assignment with an expiration time.

### How DHCP Works (DORA Process)

![[DORA.png]]

The DHCP process is known as the **DORA** process, which consists of four steps:

1. **Discover**  
   - The client sends a broadcast message to find available DHCP servers.  
   - It does not yet have an IP address, so this is sent to `255.255.255.255`.

2. **Offer**  
   - The DHCP server responds with an IP lease offer.  
   - This includes the IP address, subnet mask, gateway, lease duration, and DNS info.

3. **Request**  
   - The client replies with a broadcast request indicating that it wants to accept the offer.  
   - This confirms the chosen server if multiple responded.

4. **Acknowledge**  
   - The server confirms the IP assignment and finalizes the lease.  
   - The client can now use the IP address.

### Benefits of DHCP  
- Simplifies network administration.  
- Prevents IP conflicts caused by manual settings.  
- Speeds up the process of connecting new devices.  
- Supports both IPv4 and IPv6.

---

## Key Differences Between Routing and Switching

| Feature        | Switching                              | Routing                                 |
|----------------|------------------------------------------|------------------------------------------|
| OSI Layer      | Layer 2 – Data Link                     | Layer 3 – Network                        |
| Works With     | MAC Address                             | IP Address                               |
| Function       | Within a local network (LAN)            | Between different networks               |
| Device Used    | Switch                                  | Router                                   |
| Speed          | Faster (local traffic only)             | Slower (due to path computation)         |
| Example        | Connects devices in an office LAN       | Connects LAN to the Internet             |
