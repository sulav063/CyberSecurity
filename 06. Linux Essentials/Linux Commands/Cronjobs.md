### Cron Management
```
crontab -e          # Edit your cron jobs
crontab -l          # List your cron jobs
crontab -r          # Remove all cron jobs
cat /etc/crontab    # View system-wide cron settings
ls /etc/cron.*      # List cron directories
```

****
### Cron Scheduling
```
echo "0 * * * * /script.sh" | crontab # Schedule script hourly
crontab -u user -e  # Edit another user's crontab
systemctl status cron # Check cron service status
```

---
## Common Cron Schedule Format

```bash
* * * * * command
- - - - -
| | | | |
| | | | +---- Day of week (0-7)
| | | +------ Month (1-12)
| | +-------- Day of month (1-31)
| +---------- Hour (0-23)
+------------ Minute (0-59)
```

### Examples

```bash
0 * * * * /script.sh        # Every hour
0 0 * * * /backup.sh        # Every day at midnight
*/5 * * * * command         # Every 5 minutes
0 9 * * 1 command           # Every Monday at 9 AM
```
