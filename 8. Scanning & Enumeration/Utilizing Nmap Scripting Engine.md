The **Nmap Scripting Engine (NSE)** is a powerful feature of Nmap that allows users to automate a wide range of networking tasks using Lua scripts. NSE scripts extend the functionality of Nmap beyond basic port scanning by enabling advanced service detection, vulnerability detection, and network discovery.
### Key Features of NSE:
- **Customizable**: Users can write their own scripts or use existing ones.
- **Automated**: Automates tasks like version detection, vulnerability scanning, brute forcing, and more.
- **Flexible**: Scripts are organized by categories such as “discovery,” “vulnerability,” “intrusive,” “safe,” and “auth.”
- **Deep Analysis**: Allows enumeration of web directories, checking for weak FTP logins, DNS enumeration, SMB info gathering, etc. 
### How NSE Works:
Nmap loads and runs one or more scripts during a scan. Each script interacts with the target based on the script’s purpose. For example, some scripts probe HTTP services for specific content, while others try to log in anonymously to FTP servers.

---

### Common NSE Use Cases:
1. **HTTP Enumeration:**  
    Enumerate common directories or files on a web server to identify admin panels, login pages, or other sensitive files.
2. **FTP Anonymous Login Check:**  
    Test whether an FTP server allows anonymous login, which is a security risk if allowed without restrictions.
3. **Vulnerability Scanning:**  
    Check if the target is vulnerable to known exploits by running vulnerability detection scripts.
---
### Example NSE Commands and Their Functions:
#### HTTP Enumeration Script
```bash
nmap --script=http-enum 192.168.1.10      # Enumerate common HTTP directories and                                            files
```

Example Output:
```bash
PORT   STATE SERVICE
80/tcp open  http
| http-enum:
|   /admin: Possible admin page
|   /login: Login page found
|_  /robots.txt: Robots file found
```
---
#### FTP Anonymous Login Check
```bash
nmap --script=ftp-anon 192.168.1.10       # Check if FTP allows anonymous login
```

Example Output:
```bash
PORT   STATE SERVICE
21/tcp open  ftp
| ftp-anon: Anonymous FTP login allowed
|_ drwxr-xr-x   2 ftp      ftp          4096 Jan  1 00:00 pub
```
---
#### SMB OS Discovery
```bash
nmap --script=smb-os-discovery 192.168.1.10   # Discover OS information via SMB
```

Example Output:
```bash
PORT    STATE SERVICE
445/tcp open  microsoft-ds
| smb-os-discovery:
|   OS: Windows 7 Professional 7601 Service Pack 1
|   Computer name: TARGET-PC
|_  System time: 2025-08-13T08:00:00+00:00
```
---
#### SSL Certificate Information
```bash
nmap --script=ssl-cert 192.168.1.10         # Retrieve SSL certificate details
```

Example Output:
```bash
PORT    STATE SERVICE
443/tcp open  https
| ssl-cert:
|   Subject: commonName=www.example.com
|   Issuer: commonName=Let's Encrypt Authority X3
|   Validity: 2025-01-01T00:00:00 to 2025-04-01T00:00:00
|_  Public Key type: rsa
```
---