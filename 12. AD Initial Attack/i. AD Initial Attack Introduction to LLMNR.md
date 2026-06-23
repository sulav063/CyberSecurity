# Introduction to LLMNR

## Overview

LLMNR (Link-Local Multicast Name Resolution) is a protocol used by Windows systems to resolve hostnames when DNS resolution fails.

If a machine cannot resolve a hostname using DNS, it broadcasts a request to the local network asking:

```text
Who has this hostname?
```

Other devices on the network may respond with the requested IP address.

---

## Why LLMNR Exists

LLMNR provides fallback name resolution when:

- DNS servers are unavailable.
- DNS records do not exist.
- Hostnames are misspelled.

---

## How LLMNR Works

1. User attempts to access a resource.
2. DNS lookup fails.
3. System sends an LLMNR multicast request.
4. Any machine on the local network can answer.

---

## Risks

Attackers can impersonate legitimate hosts and capture authentication attempts.

This can lead to:

- Credential theft
- NTLM hash capture
- Relay attacks

---

## Related Protocols

- LLMNR
- NBT-NS
- DNS

---

## Importance in Cybersecurity

LLMNR poisoning is one of the most common internal Active Directory attacks.

---
