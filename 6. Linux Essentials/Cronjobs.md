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