## SHODAN (Search Engine for Internet-Connected Devices)

Shodan is a search engine that allows users to find devices connected to the internet, such as servers, routers, webcams, and more.
### Basic Usage
You can search for exposed devices, banners, ports, or services using keywords like:
- `apache`
- `nginx`
- `ftp`
- `port:22`
- `country:NP`
### Example Usage
### 1. Search for open FTP servers in Nepal:
```bash
ftp port:21 country:NP
```

### 2. Search for Apache servers in Nepal:
```bash
apache country:NP
```

### 3. Find Cisco devices:
```bash
cisco
```

### 4. Explore Amazon domain on Shodan:
```bash
hostname:amazon.com
```

### For SHODAN Useful Sites
- https://www.shodan.io
---
## theHarvester - OSINT Tool for Gathering Emails, Subdomains
theHarvester is used for gathering emails, subdomains, hosts, and employee names from different public sources.
### Basic Syntax 
```bash
theHarvester -d <domain> -b <source>

- `-d` : target domain
- `-b` : data source (google, bing, yahoo, brave, etc.)
```

### Example Commands Using Different Engines:

#### 1. Using Google
```bash
theHarvester -d example.edu.np -b google
```

#### 2. Using Bing
```bash
theHarvester -d examplebank.com.np -b bing
```

#### 3. Using Brave
```bash
theHarvester -d daraz.com.np -b brave
```

### 4. Using Yahoo
```bash
theHarvester -d globalcollege.edu.np -b yahoo
```

---
## Curl Commands
Use `curl` to fetch HTTP response headers:
```bash
curl -I google.com
curl -I testphp.vulnweb.com
curl -I https://www.daraz.com.np
```

---
## telnet:
Use `telnet` to check open ports manually:
```bash
telnet <host> <port>
```

---
### For TheHarvester Useful Sites

- Sources it uses internally:
    - Google
    - Bing
    - Yahoo
    - DuckDuckGo
    - LinkedIn (limited)
    - Baidu
----