Subdomain hunting is the process of finding subdomains associated with a main domain. This helps to identify additional attack surfaces that might be less secure.

---
### Purpose
- To discover additional services and applications running under the main domain.
- To find potential misconfigurations or outdated systems in subdomains.

---
### Methods
- **DNS Enumeration**
- **Automated Tools**
- **Passive Sources** (e.g., Certificate Transparency Logs)
---
### Importance in Cybersecurity
- Expands the attack surface.
- Uncovers development or staging environments.
- Helps identify forgotten assets.
---
### Common Tools and Commands
#### Subfinder
```bash
subfinder -d example.com
```

#### DNS Enumeration using dig
```bash
dig @8.8.8.8 example.com MX
dig example.com A
dig example.com NS
```

#### Amass
```bash
amass enum -d example.com
```
----
### Useful Sites
- https://crt.sh
- https://securitytrails.com
- https://www.virustotal.com