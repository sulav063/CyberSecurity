Before diving into port scanning and service enumeration, it is crucial to identify which hosts or devices are **actually alive and reachable** on the target network. This process is often called **host discovery** or **ping sweep**.

---
- **Why find live hosts?**  
    Scanning inactive or offline devices wastes time and resources. Identifying live hosts narrows down the scope of scanning and helps focus efforts on targets that respond.
- **How to find live hosts?**  
    The most common technique is sending **ICMP Echo Request** packets (commonly called "ping"). If the target responds with an **ICMP Echo Reply**, it confirms the host is up.
- However, some hosts may block or ignore ICMP packets due to firewall rules or configurations. In such cases, alternative methods are used:
    - Sending **TCP SYN packets** to common ports (like 80 or 443) and checking for SYN-ACK responses.
    - Sending **ARP requests** on local networks.
    - Using **UDP probes** on certain ports.
---
- **Types of scanning for live hosts:**
    - **Ping Sweep:** Send ICMP Echo Requests to a range of IPs.
    - **ARP Sweep:** Effective only on local subnet, sends ARP requests to detect MAC addresses
    - **TCP SYN Ping:** Send TCP SYN packets to specific ports; alive hosts respond with SYN-ACK.
    - **Nmap Ping Scan:** Combines several techniques to detect hosts.
---
## Common Commands and Examples

---
### Summary
|Method|Description|Use Case|Limitations|
|---|---|---|---|
|ICMP Ping|Send ICMP Echo Requests|Basic host discovery|Blocked by firewall|
|TCP SYN Ping|Send SYN packets to common ports|When ICMP blocked|Requires open ports on target|
|ARP Scan|Send ARP requests on local network|Local subnet scanning|Only works on local network|
|Nmap Ping Scan|Combines multiple techniques|Reliable detection of live hosts|May be slower due to multiple checks|

---

