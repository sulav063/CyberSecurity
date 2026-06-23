# Components of Active Directory

## Overview

Active Directory consists of multiple components that work together to manage users, systems, and resources.

---

## Domain

A domain is a logical grouping of users, computers, and resources.

Example:

```text
company.local
```

---

## Domain Controller (DC)

A Domain Controller stores:

- User accounts
- Password hashes
- Policies
- Authentication information

It handles:

- Login requests
- Kerberos tickets
- User management

---

## Forest

A forest is the highest level structure in Active Directory.

A forest can contain multiple domains.

---

## Tree

A tree is a collection of domains sharing a common namespace.

Example:

```text
company.local
dev.company.local
hr.company.local
```

---

## Organizational Units (OU)

OUs are containers used to organize:

- Users
- Computers
- Groups

Example:

```text
IT Department
HR Department
Finance Department
```

---

## Objects

Objects are entities stored inside Active Directory.

Examples:

- Users
- Computers
- Printers
- Groups

---

## Groups

Groups simplify permission management.

Examples:

- Domain Admins
- Domain Users
- Enterprise Admins

---

## DNS

Active Directory heavily relies on DNS.

DNS helps clients locate:

- Domain Controllers
- Services
- Resources

---

## Importance in Cybersecurity

Attackers commonly target:

- Domain Controllers
- Domain Admin accounts
- Misconfigured groups

---

## Key Takeaways

- Domains contain objects.
- Forests contain domains.
- OUs organize resources.
- Domain Controllers perform authentication.