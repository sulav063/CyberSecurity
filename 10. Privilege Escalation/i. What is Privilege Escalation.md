
## Privilege Escalation

Privilege escalation is the process of gaining higher-level access or permissions on a system than originally obtained.  

After an attacker gets an initial foothold (e.g., a normal user shell), they attempt to escalate privileges to **Administrator** (Windows) or **root** (Linux).  

This step allows full system control, access to sensitive data, and the ability to maintain persistence.

------
## Why It Matters (Course Context)

- Enables full exploitation of compromised hosts.
- Often needed to extract credentials (e.g., hashes, tokens) and access system-level data (NTDS.dit, /etc/shadow).
- Demonstrates impact to stakeholders: show how a low-privileged compromise becomes a full breach.
- Critical for writing accurate findings and remediation in pentest reports.

---
### Cross-platform quick checks
```bash
whoami
id
hostname
uname -a
ps aux | less
env
```


---
## Linux-specific enumeration
```bash
sudo -l                                # list sudo privileges
getent passwd                          # list user accounts
cat /etc/passwd
cat /etc/shadow                        # if readable (rare) — contains hashes
ls -la /home
find / -perm -4000 -type f 2>/dev/null  # find SUID binaries
find / -writable -type d 2>/dev/null   # writable directories
getcap -r / 2>/dev/null                # file capabilities
crontab -l                             # current user's cron
ls -la /etc/cron*                      # system cron scripts
ss -tulnp                              # listening services with PIDs
lsof -nP                              # open files and network connections
```

---
## Windows enumeration (CMD / PowerShell)
```bash
whoami
whoami /priv
systeminfo
quser / query user
tasklist /v
sc qc <ServiceName>                    # service config
Get-Service
Get-Process -IncludeUserName
schtasks /query /fo LIST /v
reg query "HKLM\SYSTEM\CurrentControlSet\Services" /s
icacls C:\path\to\file                 # check ACLs
```