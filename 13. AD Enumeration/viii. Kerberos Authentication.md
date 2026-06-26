

## Overview

Kerberos is Microsoft's primary authentication protocol used in Active Directory.

It provides secure authentication without transmitting passwords across the network.

---

# Authentication Flow

```text
User
 │
 ▼
Authentication Server
 │
 ▼
Ticket Granting Ticket (TGT)
 │
 ▼
Service Ticket
 │
 ▼
Requested Service
```

---

# Advantages

- Secure
- Fast
- Mutual Authentication
- Single Sign-On (SSO)

---

# NTLM vs Kerberos

| NTLM | Kerberos |
|------|-----------|
| Older | Modern |
| Challenge Response | Ticket Based |
| Less Secure | More Secure |

---
# Example Commands

These commands display authentication and system information.

---

## Display Current User

```bash
whoami
```

Displays the currently authenticated user.

---

## Display Current Date

```bash
date /t
```

Displays the current system date.

---

## Display Current Time

```bash
time /t
```

Displays the current system time.

---

## Display System Information

```bash
systeminfo
```

Displays general operating system information.