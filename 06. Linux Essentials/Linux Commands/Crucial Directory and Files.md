
## File Finding

```bash
find /etc -name "*.conf" 2>/dev/null    # Find configuration files in /etc
find / -perm -4000 2>/dev/null          # Find SUID files
find / -perm -2000 2>/dev/null          # Find SGID files
find / -perm -1000 2>/dev/null          # Find Sticky Bit files
locate passwd                           # Quickly locate files containing "passwd"
which python3                           # Find the location of a command
```

---

## User Information Files

```bash
cat /etc/passwd      # View user accounts
sudo cat /etc/shadow # View password hashes (root required)
cat /etc/group       # View groups
```

---

## Host Information

```bash
cat /etc/hostname    # Display system hostname
cat /etc/hosts       # View hostname-to-IP mappings
```

---

## Logs

```bash
ls /var/log              # List log files
cat /var/log/syslog      # View system logs
tail -f /var/log/syslog  # Monitor logs in real time
```

---

## Temporary Files

```bash
cd /tmp     # Move to temporary directory
ls /tmp      # List temporary files
```

---

## Shared Files and Wordlists

```bash
ls /usr/share             # List shared files
ls /usr/share/wordlists   # View Kali Linux wordlists
```

---

## Process Information

```bash
cat /proc/cpuinfo    # Display CPU information
cat /proc/meminfo    # Display memory information
echo $$              # Show current shell PID
```

---

## Device Files

```bash
ls /dev    # List device files
```

---

## Suppressing Errors

```bash
find / -name "*.txt" 2>/dev/null   # Hide permission errors
```

---

## Useful Directories

- `/home` → User home directories
- `/root` → Root user's home directory
- `/etc` → Configuration files
- `/var/log` → System logs
- `/tmp` → Temporary files
- `/usr/bin` → Installed programs
- `/usr/share` → Shared resources and wordlists
- `/proc` → Process and system information
- `/dev` → Device files
- `/opt` → Third-party software
- `/boot` → Boot files