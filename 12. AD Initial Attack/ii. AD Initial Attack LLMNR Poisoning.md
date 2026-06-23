# LLMNR Poisoning

## Overview

LLMNR Poisoning is an attack where an attacker responds to LLMNR requests and impersonates legitimate systems.

Victims unknowingly send authentication information to the attacker.

---

## Attack Flow

1. Victim requests a hostname.
2. DNS lookup fails.
3. LLMNR broadcast is sent.
4. Attacker responds first.
5. Victim sends NTLM authentication.

---

## Tools Used

Common tools include:

- Responder
- Inveigh

---

## Captured Information

Attackers may obtain:

- Usernames
- NTLM hashes

---

## Why It Works

LLMNR trusts responses from devices on the local network.

---

## Prevention

- Disable LLMNR.
- Disable NBT-NS.
- Use strong passwords.
- Implement SMB signing.

---

## Importance in Cybersecurity

LLMNR poisoning is frequently demonstrated during Active Directory penetration tests.

---
