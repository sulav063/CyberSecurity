

## What is a Networking Model?

- A **networking model** is a **conceptual framework** that defines how data is transmitted and processed across a network.
- It breaks down complex networking functions into **layers** to simplify design, communication, and troubleshooting.
- Each layer handles a specific function and communicates with the layers directly above and below it.

---

## Types of Networking Models

### 1. OSI Model (Open Systems Interconnection)
- Developed by the **International Organization for Standardization (ISO)**.
- Has **7 layers**, each with clearly defined responsibilities.
- Mainly used for learning, design, and troubleshooting network systems.

### 2. TCP/IP Model (Internet Protocol Suite)
- Developed by the U.S. Department of Defense.
- Has **4 layers** and forms the basis of the modern Internet.
- More practical and widely implemented than the OSI model.

---

# OSI Model (Open Systems Interconnection)

- The **OSI Model** is a **7-layer framework** that standardizes the functions of a networking system.
- Each layer has specific roles and interacts with the layers above and below it.

## The 7 Layers of OSI Model (from bottom to top):

### 1. Physical Layer (Layer 1)
- Deals with the **physical connection** between devices.
- Includes cables, connectors, voltage levels, and transmission of raw bits.
- **Examples:** Ethernet cables, fiber optics, network interface cards (NICs).

### 2. Data Link Layer (Layer 2)
- Responsible for **node-to-node communication** and **error detection**.
- Uses **MAC addresses** to identify devices on the same network.
- **Devices:** Switches, network interface cards.

### 3. Network Layer (Layer 3)
- Handles **routing** and **logical addressing**.
- Determines the **best path** for data to travel between networks.
- **Protocols:** IP, ICMP; **Devices:** Routers.

### 4. Transport Layer (Layer 4)
- Provides **end-to-end communication**, reliability, and flow control.
- Ensures data is **delivered accurately and in order**.
- **Protocols:** TCP (reliable), UDP (faster, but unreliable).

### 5. Session Layer (Layer 5)
- Manages **sessions or connections** between applications.
- Handles setup, maintenance, and termination of sessions.

### 6. Presentation Layer (Layer 6)
- Translates data between the application and network.
- Handles **data encoding, encryption, compression**, and formatting.
- **Examples:** JPEG, SSL/TLS.

### 7. Application Layer (Layer 7)
- Closest to the end user.
- Provides **network services directly to applications**.
- **Examples:** HTTP, FTP, SMTP, DNS.

---

## OSI Model – Summary Table with Devices

| Layer | Name           | Function                                   | Examples                  | Devices/Components               |
|-------|----------------|--------------------------------------------|---------------------------|----------------------------------|
| 7     | Application    | User interface and application services     | HTTP, FTP, DNS            | Web browsers, email clients     |
| 6     | Presentation   | Data translation, encryption, compression   | JPEG, SSL, TLS            | SSL/TLS accelerators             |
| 5     | Session        | Session control and management              | API sessions, NetBIOS     | Firewalls, application gateways |
| 4     | Transport      | Reliable delivery, error checking           | TCP, UDP                  | Gateways, firewalls             |
| 3     | Network        | Routing and logical addressing              | IP, ICMP, Routers         | Routers                         |
| 2     | Data Link      | MAC addressing and frame-level delivery     | Ethernet, MAC, VLAN       | Switches, bridges               |
| 1     | Physical       | Transmission media and physical signals     | Bits, RJ-45, LAN cables   | Ethernet cables, hubs, NICs     |


---
# TCP/IP Model (Internet Protocol Suite)

The **TCP/IP Model** is a practical framework that governs how data is sent and received over the Internet. It consists of **4 layers**, each responsible for specific functions in the communication process.

---

## 🔷 1. Application Layer
- Closest to the user.
- Handles **high-level protocols**, issues of representation, encoding, and dialog control.
- Provides services like email, file transfer, web browsing, etc.
- **Examples:** HTTP, FTP, SMTP, DNS, SNMP, Telnet

---

## 🔷 2. Transport Layer
- Provides **end-to-end communication**, **error detection**, and **flow control**.
- Responsible for breaking messages into segments and ensuring delivery.
- Uses **port numbers** to manage multiple conversations.
- **Protocols:**
  - **TCP (Transmission Control Protocol)** – Reliable, connection-oriented
  - **UDP (User Datagram Protocol)** – Faster, connectionless

---

## 🔷 3. Internet Layer
- Responsible for **logical addressing**, **routing**, and **packet forwarding**.
- Ensures data reaches the correct destination across networks.
- **Protocols:** IP (IPv4/IPv6), ICMP, ARP, IGMP
- **Devices:** Routers

---

## 🔷 4. Network Access Layer (Link Layer)
- Deals with the **physical transmission** of data over the network.
- Includes hardware addressing and access to transmission media.
- Combines functionalities of the OSI **Data Link** and **Physical Layers**.
- **Examples:** Ethernet, Wi-Fi, Frame Relay
- **Devices:** NICs, switches, hubs, cables

---

## Summary Table

| TCP/IP Layer       | OSI Equivalent Layers     | Function Summary                                | Protocols/Examples             |
|--------------------|---------------------------|--------------------------------------------------|--------------------------------|
| Application        | Application, Presentation, Session (Layers 7–5) | User interface, services, data formatting        | HTTP, FTP, SMTP, DNS           |
| Transport          | Transport (Layer 4)        | Reliable or fast delivery, error checking        | TCP, UDP                       |
| Internet           | Network (Layer 3)          | Logical addressing, routing                      | IP, ICMP, ARP                  |
| Network Access     | Data Link + Physical (Layers 2–1) | Physical transmission, hardware addressing        | Ethernet, Wi-Fi, MAC, RJ-45    |

---

## Key Differences: OSI vs TCP/IP

| Feature               | OSI Model (7 Layers)             | TCP/IP Model (4 Layers)         |
|-----------------------|----------------------------------|----------------------------------|
| Developed by          | ISO                              | U.S. Department of Defense       |
| Use                   | Theoretical reference model      | Practical, used in real networks |
| Layers                | 7                                | 4                                |
| Layer Separation      | Clear distinction between all layers | Some layers combined             |
| Common Usage          | Education, diagnostics           | Internet communication           |

