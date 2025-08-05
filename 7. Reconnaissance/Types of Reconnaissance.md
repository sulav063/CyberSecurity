### 1. Passive Reconnaissance

This is a **silent information-gathering phase** where the attacker does **not directly connect or probe** the target’s systems. Instead, they use data that is already publicly available. Since there is no interaction with the target infrastructure, this method is highly stealthy and usually impossible for the target to detect.

**Key sources used in passive recon:**

- **Search engines:** Browsing Google, Bing, DuckDuckGo, etc. to find indexed web pages, documents, cached files, and hidden directories.
- **Public records:** Domain registration details using tools like `whois`, DNS information, IP allocation records, etc.
- **Social media:** Looking at profiles on LinkedIn, Facebook, Twitter etc. to find employee names, emails, job roles, or company details.
- **Websites:** Reading the target’s websites, blogs, PDFs, or published reports to learn technology stacks, infrastructure names, partners, or internal terminology.
- **Third-party services:** Using platforms like Shodan, Censys, VirusTotal, or data breach dumps to discover exposed devices, services, or leaked credentials.

Passive reconnaissance is mainly used to **build a profile** of the target while remaining undetected. It helps map out the overall structure, potential weaknesses, and valuable information before deciding whether active techniques are needed.

### Passive Reconnaissance — Tools & Sample Usage

| Tool / Source      | Purpose                                | Example Command / Use Case                           |
|--------------------|----------------------------------------|------------------------------------------------------|
| Google Hacking     | Find hidden information via search      | `site:example.com filetype:pdf "confidential"`       |
| `whois`            | Domain registration & owner info        | `whois example.com`                                 |
| `NSlookup` / `dig` | DNS records, IP, subdomains             | `nslookup example.com`  or  `dig example.com ANY`    |
| Shodan / Censys    | Search exposed IoT & services online    | Searching **"example.com"** on <https://shodan.io>   |
| Social Media       | Employee names, roles, emails           | Browsing LinkedIn employee list                      |
| Breach Databases   | Leaked credentials                      | Checking `haveibeenpwned.com` for email leaks         |

---

### 2. Active Reconnaissance

In this stage, the attacker **directly interacts with the target’s systems or network** to extract detailed information. This sends packets to the target, so there is a chance that intrusion detection systems or logs might record the activity.

**Common active recon activities:**

- **Network scans:** Discover live hosts in a network range using tools like `nmap` or `angry IP scanner`.
- **Port scans:** Identify open ports on a machine (such as 22, 80, 443), which reveals running services and possible entry points.
- **Ping sweeps:** Send ICMP echo requests to multiple IPs to see which hosts respond and are reachable.
- **Service enumeration:** Extract service banners or metadata to identify the software version, such as web server type (Apache, Nginx), SSH version, FTP server details, etc.

Active reconnaissance provides **more accurate and rich data**, such as exact service versions, response behavior, and system configurations, but it comes with higher risk. If not done carefully, the target may detect the scans and block or log the attacker.
### Active Reconnaissance — Tools & Sample Commands

| Tool               | Purpose                                  | Example Command                                                |
|--------------------|------------------------------------------|----------------------------------------------------------------|
| `nmap`             | Host discovery & port scanning            | `nmap -sS -T4 -p- 192.168.1.0/24`                              |
| `ping`             | Check if host is up                       | `ping 192.168.1.10`                                            |
| `traceroute`       | Trace path between attacker and target    | `traceroute example.com` (Linux)  /  `tracert example.com` (Windows) |
| `Netcat (nc)`      | Banner grabbing / manual probing          | `nc -nv example.com 80`                                        |
| `enum4linux`       | Enumerate Windows/Samba shares            | `enum4linux -a 192.168.1.5`                                    |
| `WhatWeb` / `Wappalyzer` | Detect web technologies            | `whatweb example.com`                                          |

---

