Nmap ("Network Mapper") is an open-source tool for network discovery and security auditing.  It can identify live hosts, open ports, services, OS details, and vulnerabilities.

Nmap helps in:
- **Host discovery**
- **Port scanning**
- **Service & OS detection**
- **Vulnerability assessment**

---

## Common Operators and Examples

###   Basic Nmap Scan
Scans the **1000 most common TCP ports** on a target IP.

```bash
nmap 192.168.1.10
```

**Example Output:**
```
Starting Nmap 7.93 ( https://nmap.org ) at 2025-08-13
Nmap scan report for 192.168.1.10
Host is up (0.0020s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
443/tcp  open  https
```

---
### Full Port Scan (All 65535 Ports)
```bash
nmap -p- 192.168.1.10
```
**Example Output:**
```
PORT      STATE  SERVICE
21/tcp    open   ftp
22/tcp    open   ssh
80/tcp    open   http
443/tcp   open   https
3306/tcp  open   mysql
```

---
### Scan a Specific Port Range
```bash
nmap -p1-40000 192.168.10.13
```
- `-p1-40000` → Scans ports from 1 to 40000  
**Example Output:**
```
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
3306/tcp  open  mysql
```

---
### Scan Specific Ports Only
```bash
nmap -p 22,80,443 192.168.1.10
```
**Example Output:**
```
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https
```

---
### Service Version Detection
Detects **running services and versions**:
```bash
nmap -sV 192.168.1.10
```
**Example Output:**
```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2
80/tcp   open  http    Apache httpd 2.4.38 ((Debian))
443/tcp  open  https   nginx 1.14.0
```

**Advanced Variant:**
```bash
nmap -T5 -sV 192.168.10.15   # Fast service version detection
```

---
### OS Detection
```bash
nmap -O 192.168.1.10
```
**Example Output:**
```
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop
```

**Combined with Service Detection:**
```bash
nmap -T5 -O -sV 192.168.150.15
```

---
### Aggressive Scan (OS + Versions + NSE + Traceroute)
```bash
nmap -A 192.168.1.10
```
**Example Output:**
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.9p1 Debian
| ssh-hostkey:
|   2048 01:23:45:67:89:ab:cd:ef
80/tcp open  http    Apache httpd 2.4.38
| http-server-header: Apache/2.4.38 (Debian)
|_http-title: Apache2 Debian Default Page: It works
443/tcp open  https   nginx 1.14.0
```

**Aggressive + Fast Timing:**
```bash
nmap -T5 -A 192.168.150.131
```

---
### Fast Scans with Timing Templates
- `-T4` → Faster than normal  
- `-T5` → **Insane speed**, less stealthy  

**Examples:**
```bash
nmap -T4 192.168.1.10
nmap -T5 -p- 192.168.10.11
```

---
### UDP Port Scan
```bash
nmap -sU 192.168.1.10
```
**Example Output:**
```
PORT    STATE         SERVICE
53/udp  open          domain
123/udp open          ntp
161/udp open          snmp
```

---
### Vulnerability Scan with NSE
```bash
nmap --script=vuln 192.168.1.10
```
**Example Output:**
```
PORT   STATE SERVICE
80/tcp open  http
|_http-vuln-cve2017-5638: Apache Struts2 RCE vulnerability
```

---
### Save Output to File
```bash
nmap -T5 -oN metasploitable 192.168.150.131
```
- `-oN` → Save output in **normal format**

---
##  Quick Command Recap
```
nmap -p1-40000 192.168.10.13    → Port range scan
nmap -p- 192.168.10.11          → All ports
nmap -T5 -p- 192.168.10.11      → Fast full scan
nmap -sV 192.168.150.131        → Service version detection
nmap -T5 -sV 192.168.10.15      → Service version + fast timing
nmap -T5 -O -sV 192.168.150.15  → OS + service detection
nmap -T5 -A 192.168.150.131     → Aggressive scan
nmap -T5 -oN metasploitable 192.168.150.131 → Save output
```

---

