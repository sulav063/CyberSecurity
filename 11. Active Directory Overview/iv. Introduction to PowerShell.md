# Introduction to PowerShell

## Overview

PowerShell is Microsoft's command-line shell and scripting language.

It is widely used for:

- System administration
- Automation
- Active Directory management

---

## Display PowerShell Version

```powershell
$PSVersionTable
```

---

## Display Current User

```powershell
whoami
```

---

## Display Current Directory

```powershell
pwd
```

---

## List Files

```powershell
ls
```

or

```powershell
Get-ChildItem
```

---

## Change Directory

```powershell
cd Desktop
```

---

## Create File

```powershell
New-Item file.txt
```

---

## Display File Content

```powershell
Get-Content file.txt
```

---

## Running Scripts

```powershell
.\script.ps1
```

---

## Display Running Processes

```powershell
Get-Process
```

---

## Display Services

```powershell
Get-Service
```

---

## Importance in Cybersecurity

PowerShell is heavily used by:

- System administrators
- Penetration testers
- Threat actors

Many Windows attacks involve PowerShell.

---

## Key Takeaways

- PowerShell is powerful and scriptable.
- Used extensively in Windows environments.
- Essential for Active Directory administration.