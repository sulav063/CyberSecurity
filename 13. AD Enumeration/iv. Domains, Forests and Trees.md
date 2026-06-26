

## Domain

A Domain is a logical grouping of network resources managed under a common database.

Examples include:

- Users
- Computers
- Groups

---

## Tree

A Tree is one or more domains connected together using a hierarchical namespace.

Example

```
company.com

sales.company.com

it.company.com
```

---

## Forest

A Forest is the collection of one or more Trees sharing the same Active Directory schema.

```text
Forest
│
├── company.com
│
├── sales.company.com
│
└── hr.company.com
```

---

# Comparison

| Domain | Tree | Forest |
|---------|------|---------|
| Smallest logical unit | Collection of domains | Collection of trees |
| Authentication boundary | Namespace | Highest AD level |

---

# Example Commands

These commands display basic domain and network information.

---

## Display Current Domain

```bash
echo %USERDOMAIN%
```

Displays the domain name of the current logged-in user.

---

## Display DNS Configuration

```bash
ipconfig /all
```

Shows DNS servers, DNS suffixes, and other network configuration details.

---

## Display Computer Name

```bash
hostname
```

Displays the current computer hostname.