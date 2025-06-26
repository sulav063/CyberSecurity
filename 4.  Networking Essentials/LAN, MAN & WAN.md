# Types of Networks

## LAN (Local Area Network)
- A **LAN** connects devices within a limited area such as a home, office, lab, or school.
- Commonly used for file sharing, printers, applications, and internet access within the organization.

### Security Considerations:
- LANs are more secure by default because they operate in a **controlled environment**.
- However, threats like **internal attacks**, **unauthorized access**, and **malware spread** are still risks.
- **Security Measures**:
  - Strong password policies and access controls
  - Antivirus and endpoint protection
  - Network segmentation (e.g., using VLANs)
  - Firewalls for monitoring and filtering traffic
  - Physical security of network equipment

---

## MAN (Metropolitan Area Network)
- A **MAN** connects multiple LANs across a city or campus (e.g., university networks, city-wide public Wi-Fi).
- It often uses high-speed fiber connections or leased lines.

### Security Considerations:
- Broader exposure increases risk of **data interception**, **unauthorized access**, and **DDoS attacks**.
- **Public infrastructure** (shared by organizations) increases complexity.
- **Security Measures**:
  - Strong encryption for data in transit (e.g., IPsec, VPNs)
  - Access control lists (ACLs)
  - Continuous network monitoring
  - Firewalls and intrusion detection systems (IDS)

---

## WAN (Wide Area Network)
- A **WAN** connects networks over long distances — across cities, countries, or continents.
- The Internet is the largest example of a WAN.
- Used by multinational companies, cloud services, or branch offices.

### Security Considerations:
- **Highly vulnerable** to cyber threats like:
  - Data breaches
  - Man-in-the-middle (MITM) attacks
  - Spoofing, eavesdropping, ransomware
- Data travels over **public or third-party infrastructure**, increasing exposure.

- **Security Measures**:
  - Use of **VPNs** to ensure secure remote access
  - **Strong encryption** (SSL/TLS, AES)
  - Use of **secure tunneling protocols** (e.g., IPSec, GRE)
  - **Zero Trust Architecture** (never trust, always verify)
  - Cloud security tools for SaaS-based WAN services (e.g., SASE, CASB)

---

## Summary

| Network Type | Coverage Area         | Cybersecurity Risks                  | Key Protections                            |
|--------------|------------------------|--------------------------------------|--------------------------------------------|
| **LAN**      | Small (home/office)    | Internal threats, malware, access    | Firewalls, antivirus, access controls      |
| **MAN**      | Medium (city/campus)   | Data interception, shared lines      | Encryption, ACLs, IDS                      |
| **WAN**      | Large (global/Internet)| High risk: MITM, DDoS, remote threats| VPNs, TLS/SSL, Zero Trust, advanced firewalls |

