
These are hardware components used to connect, manage, and secure communication between computers and other devices in a network.

## 1. Router
- Connects different networks (e.g., home network to the internet).
- Routes data packets between networks using IP addresses.
- Can provide firewall, NAT, and DHCP functions.
- **Example:** Home router connects your LAN to your ISP.

## 2. Switch
- Connects devices within a **Local Area Network (LAN)**.
- Operates at the **Data Link Layer (Layer 2)**.
- Learns MAC addresses and forwards data only to the intended recipient.
- More efficient and secure than hubs.

## 3. Hub
- Basic networking device that broadcasts data to **all** connected devices.
- Works at **Layer 1 (Physical Layer)**.
- No intelligence — creates network collisions.
- Mostly **obsolete** today, replaced by switches.

## 4. Modem
- Converts **digital signals** to **analog** (modulation) and vice versa (demodulation).
- Allows internet access over telephone lines, fiber, or cable.
- Connects your home network to your ISP.

## 5. Firewall
- A **security device** (hardware or software) that monitors and filters network traffic.
- Allows or blocks traffic based on predefined security rules.
- Protects against **unauthorized access**, malware, and intrusions.

## 6. Access Point (AP)
- Allows **wireless devices (Wi-Fi)** to connect to a **wired LAN**.
- Acts as a bridge between wireless clients and wired network infrastructure.
- Used to expand wireless coverage.

## 7. Repeater
- **Boosts or regenerates signals** in a network to extend the transmission distance.
- Used in long-distance or weak signal scenarios.
- Works at the **Physical Layer (Layer 1)**.

## 8. Bridge
- Connects and filters traffic between two network segments.
- Operates at the **Data Link Layer (Layer 2)**.
- Can reduce collisions and divide networks logically.
- Less common today, often replaced by switches.

## 9. NIC (Network Interface Card)
- Hardware component (internal or external) that allows a device to connect to a network.
- Each NIC has a **unique MAC address**.
- Can be wired (Ethernet NIC) or wireless (Wi-Fi NIC).

---

| Device        | Function                                       | OSI Layer       |
|---------------|------------------------------------------------|-----------------|
| Router        | Connects different networks, routes data       | Network (3)     |
| Switch        | Forwards data within LAN using MAC addresses   | Data Link (2)   |
| Hub           | Broadcasts data to all devices                 | Physical (1)    |
| Modem         | Converts analog ↔ digital signals              | Physical (1)    |
| Firewall      | Monitors and filters traffic for security      | Varies (3–7)    |
| Access Point  | Connects wireless devices to a wired network   | Data Link (2)   |
| Repeater      | Amplifies or regenerates signals               | Physical (1)    |
| Bridge        | Connects network segments, filters traffic     | Data Link (2)   |
| NIC           | Connects a device to a network                 | Data Link (2)   |
