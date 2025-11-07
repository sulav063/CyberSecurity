
**IP Address** stands for **Internet Protocol Address** and serves as a unique identifier for devices on a network. It enables devices to locate and communicate with each other over networks such as the Internet or private LANs.
ipconfig, ifconfig

---

## Types of IP Addresses

### 1. IPv4 (Internet Protocol version 4)
- Uses a **32-bit address** format.
- Written as four decimal numbers separated by dots (dotted-decimal notation), e.g., `192.168.1.1`.
- Supports about **4.3 billion unique addresses**.
- Widely used but running out of available addresses due to the growth of the Internet.
- Example format: `192.0.2.1`

### 2. IPv6 (Internet Protocol version 6)
- Uses a **128-bit address** format.
- Written as eight groups of four hexadecimal digits separated by colons, e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.
- Designed to replace IPv4 and provide a vastly larger address space (approximately \(3.4 \times 10^{38}\) addresses).
- Includes improvements like simplified header format, built-in security (IPsec), and better support for mobile devices.

---

## Additional Concepts

- **Public IP Address:** Assigned to devices that are directly accessible over the Internet.
- **Private IP Address:** Used within private networks (e.g., home, office) and not routable on the Internet.
- **Static IP Address:** Manually assigned and does not change.
- **Dynamic IP Address:** Assigned automatically by DHCP and can change over time.

---

## Summary Table

| Feature          | IPv4                     | IPv6                          |
|------------------|--------------------------|-------------------------------|
| Address Length   | 32 bits                  | 128 bits                      |
| Format           | Dotted decimal (e.g., 192.168.1.1) | Hexadecimal colon-separated (e.g., 2001:db8::1) |
| Address Space    | ~4.3 billion addresses   | Vastly larger (~3.4×10^38)    |
| Header Complexity| Simpler                  | More complex but efficient    |
| Security         | Optional (IPsec optional)| Built-in IPsec support        |
| Deployment       | Widely used              | Increasing adoption worldwide |

