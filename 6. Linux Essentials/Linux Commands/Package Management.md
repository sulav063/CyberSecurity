### Package Management
```
sudo apt update          # Refresh package lists
sudo apt upgrade -y      # Upgrade installed packages
sudo apt full-upgrade -y # Upgrade with dependency handling
apt search package       # Search for a package
sudo apt install pkg     # Install a package
sudo apt remove pkg      # Remove a package
sudo apt purge pkg       # Remove package and configs
dpkg -i package.deb      # Install .deb package
dpkg -l                  # List installed packages
```

****
### Service Management
```
systemctl start service # Start a service
systemctl stop service  # Stop a service
systemctl restart service # Restart a service
systemctl status service # Check service status
service service_name start # Alternative service start
```

****

### Process Management
```
ps aux              # List all running processes
top                 # Display real-time process info
htop                # Interactive process viewer
kill pid            # Terminate process by ID
killall process_name # Terminate all processes by name
pgrep process_name  # Find process ID by name
```