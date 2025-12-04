
### 1. Vertical Privilege Escalation (Privilege Elevation)

- Definition: Move from a lower privilege level to a higher one (user → root/Administrator).
- Goal: Obtain administrative/system control.

### 2. Horizontal Privilege Escalation (Privilege Transfer)

- Definition: Move to a different account with similar privilege level but different access (userA → userB).
- Goal: Access resources available to that other account (files, databases, services).

### 3. Local vs Domain (Windows-specific)
- Local escalation: Gain local Administrator or SYSTEM on a host.
- Domain escalation: Acquire credentials or privileges enabling domain control (e.g., domain admin).