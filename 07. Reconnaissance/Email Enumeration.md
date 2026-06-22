
## Overview

Email Enumeration is the process of gathering information about email addresses associated with an organization or domain.

This information can help identify:

- Employees
- Usernames
- Mail servers
- Potential phishing targets

---

## Why Email Enumeration Matters

Organizations often expose employee emails through:

- Websites
- Social media
- Public documents
- Data breaches

Attackers may use this information for:

- Phishing
- Password spraying
- Social engineering

---

## WHOIS Information

```bash
whois example.com
```

Displays:

- Domain owner
- Registrar
- Contact information
- Name servers

Install if missing:

```bash
sudo apt install whois
```

---

## theHarvester

TheHarvester collects:

- Emails
- Subdomains
- Hosts
- Usernames

Example:

```bash
theHarvester -d example.com -b all
```

Use Google:

```bash
theHarvester -d example.com -b google
```

Use Bing:

```bash
theHarvester -d example.com -b bing
```

Install:

```bash
sudo apt install theharvester
```

---

## Hunter.io

Search for emails associated with a domain.

Example:

```text
example.com
```

May reveal:

- Employee emails
- Naming conventions

Examples:

- john@example.com
- admin@example.com

---

## Search Engines

Google dorks can reveal email addresses.

Example:

```text
site:example.com "@example.com"
```

Example:

```text
site:example.com email
```

---

## Public Documents

PDF files sometimes contain email addresses.

Useful extensions:

```text
filetype:pdf
filetype:docx
filetype:xlsx
```

Example:

```text
site:example.com filetype:pdf
```

---

## Breach Databases

Public breach databases may reveal:

- Emails
- Usernames
- Password reuse

Examples:

- Have I Been Pwned
- DeHashed

---

## Email Format Discovery

Common patterns:

```text
firstname.lastname@example.com
first.last@example.com
f.lastname@example.com
firstname@example.com
```

Examples:

```text
john.doe@example.com
j.doe@example.com
admin@example.com
```

---

## MX Records

Mail servers can be identified with:

```bash
dig example.com MX
```

or

```bash
host -t MX example.com
```

---

## SMTP Enumeration

Check SMTP service:

```bash
nc example.com 25
```

Common ports:

- 25
- 465
- 587

---

## Importance in Cybersecurity

Email enumeration assists in:

- OSINT investigations
- Social engineering assessments
- Red team engagements
- Attack surface mapping

---

## Key Takeaways

- Email addresses are valuable OSINT information.
- theHarvester automates email discovery.
- WHOIS records may reveal contact information.
- MX records identify mail servers.
- Public documents often leak email addresses.