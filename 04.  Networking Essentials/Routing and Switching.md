
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
Routing is the process of directing data **between different networks** using **IP addresses**. It ensures that data packets take the best path to reach their destination.
### OSI Layer  
Routing operates at **Layer 3 – Network Layer** of the OSI model.

### Key Concepts

- **Router**:  
  A device that connects multiple networks and determines the best path for data to travel between them.  
  It examines the **IP header** and makes forwarding decisions based on the **routing table**.

- **Routing Table**:  
  A data table stored in a router or Layer 3 device that lists routes to particular network destinations.  
  It contains:
  - Destination network
  - Subnet mask
  - Next hop IP
  - Interface
  - Metric/cost

- **Hop**:  
  A **hop** refers to the passage of a data packet from one network device (router) to another.  
  Each router a packet passes through counts as one hop.

- **Route**:  
  A **route** defines a path from the source network to the destination network.  
  Routes are stored in the routing table and can be manually or dynamically created.

### Types of Routing

| Type            | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| **Static Routing**  | Manually configured routes. Simple, secure, but not scalable.              |
| **Dynamic Routing** | Automatically updated by routers using routing protocols. Adaptable.      |
| **Default Routing** | A static route used when no other route is found (often to the internet). |


### Dynamic Routing Protocols

Dynamic routing protocols help routers discover and update routes automatically. They fall into three main categories:

#### 1. **Distance Vector Protocols**
- Share full routing tables periodically with neighbors.
- Choose the best path based on **hop count**.
- Slower convergence and risk of routing loops.
- **Example**: RIP (Routing Information Protocol)

#### 2. **Link State Protocols**
- Routers exchange **state of their links (interfaces)**.
- Builds a full map of the network.
- Fast convergence and more accurate.
- **Example**: OSPF (Open Shortest Path First), IS-IS

#### 3. **Path Vector Protocols**
- Designed for **interdomain routing** (e.g., Internet).
- Maintains the path information that gets updated dynamically.
- Used in very large networks.
- **Example**: BGP (Border Gateway Protocol)

### Workflow of Routing (Simplified)

1. **Packet Creation**  
   The source device creates a packet with destination IP.

2. **Check Network**  
   The source checks if the destination is in the same network.  
   If not, it sends the packet to its **default gateway** (router).

3. **Routing Table Lookup**  
   The router receives the packet and checks its **routing table**.

4. **Select Next Hop**  
   Based on the destination IP, it selects the best route and forwards the packet to the **next hop**.

5. **Repeat**  
   This process repeats across routers until the packet reaches the destination.

6. **Delivery**  
   The destination device receives the packet and responds.

### Example Scenario

- Device A (192.168.1.10) wants to send data to Server B (10.0.0.5).
- Device A sends the packet to its router (default gateway).
- The router examines its routing table:
  - If it has a route to 10.0.0.0/8 → forwards to the next hop.
  - If no specific route exists → uses a **default route** (0.0.0.0/0).
- The packet is passed through routers until it reaches 10.0.0.5.

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
