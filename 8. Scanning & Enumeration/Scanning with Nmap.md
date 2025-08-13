Nmap ("Network Mapper") is a powerful open-source tool for network discovery and security auditing. It helps identify live hosts, open ports, running services, versions, and possible vulnerabilities.

---
### Common Operators and Examples
#### Basic Nmap Scan
```bash
nmap 192.168.1.10                             # Scan the 1000 most common TCP                                                    ports on target IP
```

Example Output:
```bash
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
#### Full Port Scan
```bash
nmap -p- 192.168.1.10                         # Scan all 65535 TCP ports on target                                               IP
```

Example Output:
```bash
PORT      STATE  SERVICE
21/tcp    open   ftp
22/tcp    open   ssh
80/tcp    open   http
443/tcp   open   https
3306/tcp  open   mysql
```
---
#### Service Version Detection
```bash
nmap -sV 192.168.1.10                         # Detect running services and                                                      versions on open ports
```

Example Output:
```bash
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
80/tcp   open  http    Apache httpd 2.4.38 ((Debian))
443/tcp  open  https   nginx 1.14.0
```
---
#### Operating System Detection
```bash
nmap -O 192.168.1.10                          # Detect the OS of the target machine
```

Example Output:
```bash
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop
```
---
#### Aggressive Scan (OS, versions, scripts, traceroute)
```bash
nmap -A 192.168.1.10                          # Detailed scan with OS detection,                                                 version detection, NSE scripts,                                                    traceroute
```

Example Output:
```bash
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey:
|   2048 01:23:45:67:89:ab:cd:ef:01:23:45:67:89:ab:cd:ef (RSA)
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
| http-server-header: Apache/2.4.38 (Debian)
|_http-title: Apache2 Debian Default Page: It works
443/tcp open  https   nginx 1.14.0
```
---
#### Vulnerability Scan with NSE Scripts
```bash
nmap --script=vuln 192.168.1.10               # Scan for known vulnerabilities                                                   using NSE scripts
```

Example Output:
```bash
PORT   STATE SERVICE
80/tcp open  http
|_http-vuln-cve2017-5638: Apache Struts2 Remote Code Execution vulnerability
```
---
####  UDP Port Scan
```bash
nmap -sU 192.168.1.10                         # Scan UDP ports on the target IP
```

Example Output:
```bash
PORT    STATE         SERVICE
53/udp  open          domain
123/udp open          ntp
161/udp open          snmp
```
---
#### Scan Specific Ports Only
```bash
nmap -p 22,80,443 192.168.1.10                # Scan only ports 22, 80, and 443
```

Example Output:
```bash
PORT    STATE SERVICE
22/tcp  open  ssh`
80/tcp  open  http
443/tcp open  https
```
---
#### Scan with Increased Speed
```bash
nmap -T4 192.168.1.10                         # Scan with faster timing template                                                 (less stealthy)
```
---