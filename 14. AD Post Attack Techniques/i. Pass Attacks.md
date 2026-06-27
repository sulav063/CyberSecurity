
## Overview

Pass Attacks are authentication-based attacks that abuse stored credentials, password hashes, or authentication tokens instead of cracking passwords directly.

The attacker attempts to reuse authentication material rather than discovering the original password.

---

## Why They Are Dangerous

Traditional security focuses on protecting passwords.

However, modern authentication systems also rely on:

- Password Hashes
- Authentication Tokens
- Tickets
- Session Credentials

If these are stolen, they may be abused without knowing the actual password.

---

## Authentication Flow

```text
User
 │
 ▼
Authentication
 │
 ▼
Credential Material
 │
 ▼
Access Granted
```

---

## Common Types

### Pass-the-Hash

Uses a password hash instead of the plaintext password.

---

### Pass-the-Ticket

Uses authentication tickets issued by Kerberos.

---

### Token Abuse

Uses valid authentication tokens.

---

## Prevention

- MFA
- Credential Guard
- Strong Password Policies
- Least Privilege
- Privileged Access Workstations

---

## Detection

- Unusual Logins
- Authentication Anomalies
- Lateral Movement Indicators
- Suspicious Account Activity

---

## Key Takeaways

- Attackers target authentication artifacts.
- Passwords are not always required.
- Monitoring authentication activity is critical.