Once live hosts and open ports are identified, the next step is to **enumerate common services** to gather detailed information about the running applications, versions, and configurations. This step is crucial for identifying potential vulnerabilities.

---
### FTP Enumeration (Port 21)
```bash
nmap -p 21 -sV 192.168.1.10
```
	- `-p 21` → Scans only FTP port.
	- `-sV` → Detects service version.
Possible Output:
```bash
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 2.3.4
```
#### Additional NSE scripts for FTP:
```bash
nmap -p 21 --script ftp-anon,ftp-banner 192.168.1.10
```
	- `ftp-anon` → Checks for anonymous login.
	- `ftp-banner` → Grabs FTP service banner.
Possible Output:
```bash
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 2.3.4
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-banner:
|   220 (vsFTPd 2.3.4)
```

---
### HTTP Enumeration (Port 80/443)
```bash
nmap -p 80 --script http-title 192.168.1.10
```
Possible Output:
```bash
PORT   STATE SERVICE
80/tcp open  http
|_http-title: Welcome to Apache!
```
#### Advanced HTTP scripts:
```bash
nmap -p 80 --script http-headers,http-methods,http-enum 192.168.1.10
```
	- `http-headers` → Shows HTTP response headers.
	- `http-methods` → Lists supported HTTP methods (GET, POST, PUT, etc.).
	- `http-enum` → Attempts to enumerate directories.
Possible Output:
```bash
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
| http-headers:
|   Server: Apache/2.4.41 (Ubuntu)
|   Content-Type: text/html; charset=UTF-8
|
| http-methods:
|   Supported Methods: GET HEAD POST OPTIONS
|
| http-enum:
|   /index.html
|   /admin/
```
---
### Service Version Scans for Enumeration
The `-sV` scan is also used to enumerate services like FTP, HTTP, SSH.
```bash
nmap -T5 -sV 192.168.10.15
```
Possible Output:
```bash
Starting Nmap 7.93 ( https://nmap.org ) at 2025-08-23 11:00 UTC
Nmap scan report for 192.168.10.15
Host is up (0.0012s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE    VERSION
21/tcp   open  ftp        vsftpd 3.0.3
22/tcp   open  ssh        OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
80/tcp   open  http       Apache httpd 2.4.41 ((Ubuntu))
443/tcp  open  https      nginx 1.14.0
3306/tcp open  mysql      MySQL 5.7.32
```