Overview

Google Dorking (Google Hacking) is the process of using advanced search operators to discover publicly accessible information indexed by search engines.

It is widely used in:

- Open Source Intelligence (OSINT)
- Penetration Testing
- Bug Bounty Hunting
- Reconnaissance

---

## Why Google Dorking Matters

Misconfigured websites may unintentionally expose:

- Login pages
- Backup files
- Configuration files
- Documents
- Cameras
- Source code

---

## Basic Search Operators

### Search Within a Website

```text
site:example.com
```

Example:

```text
site:example.com
```

---

### Search for Specific File Types

```text
filetype:pdf
```

Example:

```text
site:example.com filetype:pdf
```

Common file types:

- pdf
- docx
- xlsx
- txt

---

### Search for a Keyword in URLs

```text
inurl:admin
```

Example:

```text
site:example.com inurl:admin
```

---

### Search Page Titles

```text
intitle:login
```

Example:

```text
site:example.com intitle:login
```

---

### Search Page Contents

```text
intext:password
```

Example:

```text
site:example.com intext:password
```

---

## Finding Login Pages

```text
inurl:login
```

```text
intitle:"Login"
```

Example:

```text
site:example.com inurl:login
```

---

## Finding PDFs

```text
site:example.com filetype:pdf
```

Useful for finding:

- Manuals
- Reports
- Employee information

---

## Finding Excel Files

```text
site:example.com filetype:xlsx
```

---

## Finding Word Documents

```text
site:example.com filetype:docx
```

---

## Searching for Email Addresses

```text
site:example.com "@example.com"
```

---

## Searching for Exposed Directories

```text
intitle:"Index of"
```

Example:

```text
intitle:"Index of" backup
```

---

## Searching for Configuration Files

```text
filetype:conf
```

Example:

```text
filetype:env
```

---

## Searching for Backup Files

```text
ext:bak
ext:old
ext:zip
```

Example:

```text
site:example.com ext:zip
```

---

## Searching for Cameras

```text
inurl:view.shtml
```

```text
intitle:"webcamXP"
```

---

## Combining Operators

Example:

```text
site:example.com filetype:pdf confidential
```

Example:

```text
site:example.com inurl:admin
```

---

## Google Dork Database (GHDB)

The Google Hacking Database contains many search patterns used during reconnaissance.

Categories include:

- Files containing passwords
- Login portals
- Vulnerable applications
- Exposed databases

---

## Importance in Cybersecurity

Google Dorking helps discover:

- Hidden files
- Documents
- Login pages
- Public information leaks

---

## Key Takeaways

- Google indexes publicly accessible information.
- Search operators improve reconnaissance.
- Misconfigurations can expose sensitive files.
- Google Dorking is a powerful OSINT technique.