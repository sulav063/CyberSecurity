
## Overview

Organizational Units (OUs) are containers used to organize Active Directory objects.

They help administrators:

- Organize Users
- Organize Computers
- Apply Group Policies
- Delegate Administration

---

## Example

```text
College.local
│
├── Faculty
│
├── Students
│
├── Labs
│
└── Servers
```

---

# Advantages

- Better Organization
- Easier Management
- Group Policy Application
- Administrative Delegation

---

# Difference

| OU | Group |
|----|-------|
| Organizes objects | Collects users |
| Used for GPO | Used for permissions |

---
# Example Commands

These commands display local user and system information.

---

## Display Current User

```bash
whoami
```

Displays the current logged-in user.

---

## List Local Users

```bash
net user
```

Lists all local user accounts configured on the system.

---

## Display System Information

```bash
systeminfo
```

Displays detailed operating system information.