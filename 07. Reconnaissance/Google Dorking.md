Google Dorking (Google Hacking) is the use of advanced Google search operators to locate sensitive information on websites.

---
### Importance in Cybersecurity
- Finds misconfigured websites.
- Detects exposed credentials and documents.
---
### Common Operators and Examples
```bash
site:example.com                               # Show all indexed pages from                                                      example.com
site:amazon.com filetype:pdf                   # Search for PDFs on amazon.com
intitle:"login" site:example.com               # Find login pages
inurl:"admin" site:example.com                 # Find admin panels
filetype:xls site:example.com                  # Find Excel files (may contain                                                    credentials)
```
---
### For Google Dorking Useful Sites
- https://www.google.com
- https://www.exploit-db.com/google-hacking-database