
## Overview

DNS Enumeration is the process of collecting information from DNS servers to identify hosts, subdomains, mail servers, and other infrastructure details.

DNS information is valuable during reconnaissance because it reveals attack surfaces.

---

## Common DNS Record Types

| Record | Purpose |
|----------|---------|
| A | Maps domain to IPv4 address |
| AAAA | Maps domain to IPv6 address |
| MX | Mail servers |
| NS | Name servers |
| TXT | Additional text information |
| CNAME | Alias records |

---

## nslookup

```bash
nslookup example.com          # Lookup a domain
nslookup example.com 8.8.8.8  # Use Google's DNS server
```

---

## dig

```bash
dig example.com          # Query domain
dig example.com MX       # Query mail servers
dig example.com NS       # Query name servers
dig example.com TXT      # Query TXT records
```

---

## host

```bash
host example.com          # Resolve domain
host -t MX example.com    # Query MX records
host -t NS example.com    # Query NS records
```

---

## Reverse Lookup

```bash
host 8.8.8.8
```

Attempts to resolve an IP address back to a hostname.

---

## Zone Transfer

```bash
dig axfr @ns1.example.com example.com
```

Attempts a DNS zone transfer.

A successful zone transfer may reveal:

- Subdomains
- Internal hosts
- Mail servers

---

## Fierce

```bash
fierce --domain example.com
```

Performs DNS reconnaissance and subdomain discovery.

Install:

```bash
sudo apt install fierce
```

---

## dnsenum

```bash
dnsenum example.com
```

Performs:

- WHOIS lookup
- Reverse lookups
- Subdomain enumeration

Install:

```bash
sudo apt install dnsenum
```

---

## dnsrecon

```bash
dnsrecon -d example.com
```

Enumerates:

- A records
- MX records
- NS records
- Subdomains

Install:

```bash
sudo apt install dnsrecon
```

---

## Importance in Cybersecurity

DNS Enumeration helps identify:

- Subdomains
- Mail servers
- Hidden infrastructure
- Potential attack surfaces

---

## Key Takeaways

- DNS stores information about domains.
- dig, nslookup, and host are common tools.
- Zone transfers can expose sensitive information.
- DNS enumeration is a fundamental reconnaissance technique.