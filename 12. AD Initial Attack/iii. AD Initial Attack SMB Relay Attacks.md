# SMB Relay Attacks

## Overview

SMB Relay attacks occur when an attacker intercepts NTLM authentication and forwards it to another machine.

The attacker does not need to know the password.

---

## Requirements

Successful SMB relay attacks usually require:

- SMB signing disabled
- NTLM authentication enabled

---

## Attack Flow

1. Victim authenticates.
2. Attacker intercepts NTLM challenge-response.
3. Authentication is relayed to another host.
4. Access is granted.

---

## Potential Impact

Attackers may:

- Execute commands
- Access shares
- Gain administrative access

---

## Prevention

- Enable SMB signing.
- Disable NTLM where possible.
- Use Kerberos authentication.

---

## Importance in Cybersecurity

SMB relay attacks are common in internal assessments.

---
