
## Overview

A Domain Controller (DC) is a Windows server that stores the Active Directory database.

It performs:

- Authentication
- Authorization
- Replication
- Policy Management

---

## Responsibilities

- Verify usernames
- Verify passwords
- Store AD Database
- Replicate changes
- Apply Group Policies

---

## Authentication Flow

```text
User Login
      │
      ▼
Domain Controller
      │
      ▼
Verify Credentials
      │
      ▼
Access Granted
```

---

# Example Commands

These commands help verify basic network and system information commonly associated with Domain Controllers.

---

## Display Network Configuration

```bash
ipconfig /all
```

Displays complete network adapter configuration including DNS information.

---

## Display Hostname

```bash
hostname
```

Displays the hostname of the current computer.

---

## Test Network Connectivity

```bash
ping localhost
```

Tests the local network stack.