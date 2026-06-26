

## Overview

Active Directory (AD) is Microsoft's directory service that stores information about users, computers, groups, printers, and other network resources. It provides centralized authentication, authorization, and resource management in Windows enterprise environments.

Active Directory enables administrators to manage thousands of devices and users from a single location while enforcing security policies across the organization.

---

# Architecture

```text
                    Forest
                       │
              ┌────────┴────────┐
              │                 │
          Tree 1            Tree 2
              │
        ┌─────┴─────┐
        │           │
   Domain A     Domain B
        │
   ┌────┴────┐
   │         │
Users     Computers
   │
Groups
```

---

# Components

## Forest

A Forest is the highest level of Active Directory.

It contains:

- Multiple Trees
- Domains
- Shared Schema
- Global Catalog

---

## Tree

A Tree is a collection of domains sharing a common namespace.

Example

```
company.com

hr.company.com

it.company.com
```

---

## Domain

A Domain is the logical boundary where users, groups, computers, and policies are managed.

Example

```
college.edu
```

---

## Organizational Unit (OU)

Organizes users and computers for easier administration.

Example

```
Faculty

Students

Accounts

Servers
```

---

## Domain Controller

A Domain Controller stores the Active Directory database and authenticates users.

Responsibilities include:

- User Authentication
- Policy Enforcement
- Directory Replication

---

# Benefits

- Centralized Management
- Authentication
- Authorization
- Group Policy
- Resource Sharing
- Scalability

---
# Example Commands

These are basic Windows administrative commands related to Active Directory architecture. They help administrators verify system and domain information.

---

## Display Computer Name

```bash
hostname
```

Displays the hostname of the current computer.

---

## Display Current User

```bash
whoami
```

Displays the currently logged-in user.

---

## Display System Information

```bash
systeminfo
```

Displays detailed information about the operating system, hardware, and configuration.

---

## Display Current Domain

```bash
echo %USERDOMAIN%
```

Displays the Windows domain that the current user belongs to.