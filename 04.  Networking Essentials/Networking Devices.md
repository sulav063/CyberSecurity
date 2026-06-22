## Overview

Networking devices are hardware components that allow computers and networks to communicate with each other. Each device performs a specific role and operates at different layers of the OSI model.

---

## Hub

A hub is a basic networking device that broadcasts incoming data to every connected device.

### Characteristics

- Operates at Layer 1 (Physical Layer)
    
- Does not understand MAC addresses
    
- Sends data to all ports
    
- Rarely used today
    

### Advantages

- Simple to use
    
- Inexpensive
    

### Disadvantages

- Creates unnecessary traffic
    
- Poor security
    
- Collisions occur frequently
    

---

## Switch

A switch forwards data only to the intended device.

### Characteristics

- Operates at Layer 2 (Data Link Layer)
    
- Uses MAC addresses
    
- Maintains a MAC Address Table
    
- Reduces collisions
    

### Advantages

- Efficient communication
    
- Better performance than hubs
    
- Improved security
    

### Example

If PC A sends data to PC B, the switch sends the frame only to PC B instead of every device.

---

## Router

A router connects multiple networks together.

### Characteristics

- Operates at Layer 3 (Network Layer)
    
- Uses IP addresses
    
- Determines the best path for packets
    

### Functions

- Connects LAN to WAN
    
- Provides internet access
    
- Separates broadcast domains
    

### Example

Home Wi-Fi routers connect internal devices to the Internet.

---

## Bridge

A bridge connects two network segments.

### Characteristics

- Operates at Layer 2
    
- Uses MAC addresses
    
- Reduces collisions
    

### Purpose

Bridges divide large networks into smaller segments to improve performance.

---

## Repeater

A repeater regenerates weak signals.

### Characteristics

- Operates at Layer 1
    
- Extends transmission distance
    

### Example

Used in long cable networks where signal strength decreases.

---

## Gateway

A gateway enables communication between different network architectures.

### Functions

- Protocol translation
    
- Connecting dissimilar networks
    
- Providing access to external resources
    

### Example

A router can also function as a gateway.

---

## Modem

A modem converts:

- Digital signals → Analog signals
    
- Analog signals → Digital signals
    

### Purpose

Provides Internet connectivity through:

- DSL
    
- Cable
    
- Fiber
    

---

## Firewall

A firewall monitors and filters network traffic.

### Functions

- Block unauthorized access
    
- Allow trusted traffic
    
- Enforce security rules
    

### Types

#### Hardware Firewall

Dedicated physical device.

#### Software Firewall

Installed directly on operating systems.

Examples:

- Windows Defender Firewall
    
- UFW (Linux)
    

---

## Intrusion Detection System (IDS)

An IDS monitors traffic and generates alerts when suspicious activity is detected.

### Characteristics

- Detects attacks
    
- Does not block traffic
    

Examples:

- Snort
    
- Suricata
    

---

## Intrusion Prevention System (IPS)

An IPS actively blocks malicious traffic.

### Capabilities

- Detect attacks
    
- Automatically prevent attacks
    

---

## Access Point (AP)

An Access Point provides wireless connectivity.

### Functions

- Broadcast Wi-Fi signals
    
- Connect wireless devices to wired networks
    

Examples:

- Home Wi-Fi routers
    
- Enterprise wireless access points
    

---

## Proxy Server

A proxy acts as an intermediary between clients and servers.

### Benefits

- Hides client IP addresses
    
- Filters content
    
- Monitors traffic
    

Examples:

- Squid Proxy
    
- Burp Suite Proxy
    

---

## Load Balancer

A load balancer distributes traffic among multiple servers.

### Advantages

- High availability
    
- Better performance
    
- Fault tolerance
    

---

## Summary Table

|Device|OSI Layer|
|---|---|
|Hub|Layer 1|
|Repeater|Layer 1|
|Bridge|Layer 2|
|Switch|Layer 2|
|Router|Layer 3|
|Firewall|Layer 3/4|
|Gateway|Multiple|
|Access Point|Layer 2|
|Proxy|Layer 7|

---

## Key Takeaways

- Hubs broadcast traffic.
    
- Switches use MAC addresses.
    
- Routers use IP addresses.
    
- Firewalls filter traffic.
    
- IDS detects attacks.
    
- IPS prevents attacks.
    
- Access Points provide wireless connectivity.