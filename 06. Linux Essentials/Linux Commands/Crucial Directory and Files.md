### System File Viewing
```bash
cat /etc/passwd     # View user account info
cat /etc/shadow     # View encrypted passwords (root access)
cat /etc/hosts      # Display hosts file
cat /etc/fstab      # Show filesystem mount points
cat /var/log/syslog # Read system logs
```

****
### Log and Configuration Management
```bash
ls /var/log         # List log files
tail -f /var/log/syslog # Monitor logs in real-time
nano /etc/apt/sources.list # Edit package repositories
less /etc/passwd    # Paginated view of file
grep "pattern" /etc/passwd # Search for pattern in file
```

****

### File Finding
```bash
find /etc -name "*.conf" 2>/dev/null # Find config files in /etc
locate config.conf  # Quickly locate a file
```