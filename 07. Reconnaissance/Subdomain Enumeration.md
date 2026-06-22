
## Overview

Subdomain Enumeration is the process of discovering subdomains associated with a target domain.

Organizations often host services on different subdomains, such as:

- mail.example.com
- admin.example.com
- dev.example.com
- vpn.example.com

Finding these subdomains helps identify additional attack surfaces.

---

## Why Subdomain Enumeration Matters

Subdomains may expose:

- Login portals
- Development servers
- APIs
- Internal applications
- Forgotten assets

---

## Common Methods

### Passive Enumeration

Uses public sources without directly interacting with the target.

Examples:

- Search engines
- Certificate Transparency logs
- Security databases

### Active Enumeration

Directly queries DNS servers and brute-forces names.

---

## Assetfinder

```bash
assetfinder example.com
```

Find only subdomains:

```bash
assetfinder --subs-only example.com
```

Install:

```bash
go install github.com/tomnomnom/assetfinder@latest
```

---

## Subfinder

```bash
subfinder -d example.com
```

Save output:

```bash
subfinder -d example.com -o subs.txt
```

Install:

```bash
sudo apt install subfinder
```

---

## Amass

Passive enumeration:

```bash
amass enum -passive -d example.com
```

Active enumeration:

```bash
amass enum -active -d example.com
```

Install:

```bash
sudo apt install amass
```

---

## Gobuster DNS Mode

```bash
gobuster dns -d example.com -w wordlist.txt
```

Example:

```bash
gobuster dns -d example.com -w /usr/share/wordlists/dirb/common.txt
```

---

## FFUF DNS Enumeration

```bash
ffuf -u http://FUZZ.example.com -w wordlist.txt
```

Example:

```bash
ffuf -u http://FUZZ.example.com -w /usr/share/wordlists/dirb/common.txt
```

---

## crt.sh

Certificate Transparency logs often reveal subdomains.

Search:

```text
%.example.com
```

Useful for passive reconnaissance.

---

## DNS Zone Transfer

```bash
dig axfr @ns1.example.com example.com
```

If successful, it may reveal:

- Internal hosts
- Mail servers
- Subdomains

---

## Resolve Discovered Subdomains

```bash
host sub.example.com
```

or

```bash
nslookup sub.example.com
```

---

## Check Live Hosts

```bash
httpx -l subs.txt
```

Install:

```bash
go install github.com/projectdiscovery/httpx/cmd/httpx@latest
```

---

## Save Results

```bash
subfinder -d example.com > subdomains.txt
```

Count discovered subdomains:

```bash
wc -l subdomains.txt
```

---

## Importance in Cybersecurity

Subdomain enumeration helps discover:

- Hidden applications
- APIs
- Development environments
- Additional attack surfaces

---

