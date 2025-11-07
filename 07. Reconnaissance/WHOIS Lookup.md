WHOIS is a protocol used to retrieve domain registration information from publicly available databases. It helps identify:

- The domain owner (individual or organization)
- Registrar information
- Domain creation and expiry dates
- Contact information (administrative, technical)
- Name servers associated with the domain

Information obtained from WHOIS can be used to:

- Map the ownership structure of a target network
- Identify possible human targets (administrators, technical contacts)
- Find related domains registered by the same organization
- Trace infrastructure used by the target over time

---
### Whois Lookup
```bash
whois example.com           # Get domain registration info (owner, registrar,                                    creation/expiry)
whois amazon.com            # Check who owns the Amazon domain
whois <IP-address>          # Also works with IPs to identify allocation info

```

---

### DNS Lookup with nslookup
```bash
nslookup example.com                # Resolve domain name to IP address (default                                         query)
nslookup -type=A example.com        # Get IPv4 address
nslookup -type=AAAA example.com     # Get IPv6 address
nslookup -type=MX example.com       # Find mail exchange (mail servers)
nslookup -type=NS example.com       # Find name servers
nslookup -type=CNAME example.com    # Lookup canonical (alias) records
nslookup -type=TXT example.com      # View text records (SPF, DKIM, etc.)
```

---
### Subdomain Enumeration (subfinder)
```bash
subfinder -d example.com         # Discover subdomains of a target domain
subfinder -d example.com -silent # Quiet output (only subdomains)
subfinder -up                    # Update subfinder sources & providers
```

---
### DNS Lookup using `dig`
```bash
dig example.com                    # Basic DNS lookup (default A record)
dig @8.8.8.8 example.com           # Query using a specific DNS server (Google DNS)

dig example.com A                 # Get IPv4 address (A record)
dig example.com AAAA             # Get IPv6 address (AAAA record)
dig example.com MX               # Find mail servers (MX record)
dig example.com NS               # List name servers (NS record)
dig example.com TXT              # Get text records (SPF, DKIM, etc.)

dig +short example.com           # Show concise output (just the result)
dig +trace example.com           # Trace DNS path from root to authoritative server
```

---
