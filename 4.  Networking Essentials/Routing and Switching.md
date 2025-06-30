
Routing and switching are core functions in networking that determine how data travels within and between networks.

---

## Switching

### Definition:
Switching is the process of forwarding data **within the same network (LAN)** based on MAC addresses.

### OSI Layer:
Operates at **Layer 2 – Data Link Layer**.

### How Switching Works:
- Switches connect devices like PCs, printers, servers.
- Each device gets a dedicated port.
- Switch reads the MAC address from the data frame.
- Builds a MAC address table to identify which device is on which port.
- Forwards data only to the destination device, reducing unnecessary traffic.

### Types of Switching:
- Circuit Switching (used in traditional telephony)
- Packet Switching (used in modern networks)
- Message Switching (historical, mostly obsolete)

### Benefits of Switching:
- Reduces network collisions (compared to hubs).
- Improves performance by forwarding data selectively.
- Supports VLANs (Virtual LANs) for segmentation and security.
- Enables full-duplex communication (send and receive simultaneously).

---

## Routing

### Definition:
Routing is the process of directing data **between different networks** using IP addresses.

### OSI Layer:
Operates at **Layer 3 – Network Layer**.

### How Routing Works:
- Routers connect different networks (e.g., LAN to the internet).
- Inspect the IP header of each packet.
- Use a routing table to determine the best path.
- Forward packets to the next hop toward the destination.

### Types of Routing:

| Type           | Description                                                |
|----------------|------------------------------------------------------------|
| Static Routing | Manually configured routes; simple but lacks flexibility. |
| Dynamic Routing| Routers exchange information using routing protocols.     |

### Common Dynamic Routing Protocols:
- RIP – Uses hop count as metric; simple but slow.
- OSPF – Link-state protocol; faster and more efficient.
- BGP – Used for routing between ISPs and large networks (internet backbone).

---

## Key Differences Between Routing and Switching

| Feature       | Switching                         | Routing                             |
|---------------|------------------------------------|--------------------------------------|
| OSI Layer     | Layer 2 (Data Link Layer)          | Layer 3 (Network Layer)              |
| Works With    | MAC addresses                      | IP addresses                         |
| Function      | Forwards data within a network     | Forwards data between networks       |
| Device Used   | Switch                             | Router                               |
| Speed         | Faster (direct local traffic)      | Slower (path calculation involved)   |
| Example       | Connecting PCs in a LAN            | Connecting a LAN to the internet     |


