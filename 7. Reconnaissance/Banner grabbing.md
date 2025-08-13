Banner grabbing is the technique of collecting information from service banners. These banners reveal details such as software name, version, and operating system.

---
## Importance in Cybersecurity
- Helps in vulnerability mapping (specific versions may have known CVEs).
- Useful for fingerprinting systems.
---
## Methods
### Using curl
```bash
curl -I http://example.com
curl -I https://example.com
```
### Using telnet
```bash
telnet example.com 80
```
    
#### Using Netcat
```bash
nc example.com 80
```

#### HTTP HEAD request
```bash
curl -s -I example.com | grep Server
```
---
### Useful Sites
- No specific websites (done via tools), but you can use:
    https://pentest-tools.com (HTTP Header Checker)
---
    