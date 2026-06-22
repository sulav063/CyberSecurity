## Overview

`sudo` (Super User Do) allows a normal user to execute commands with elevated privileges.

It is commonly used for:

- Installing software
- Modifying system files
- Managing users
- Administrative tasks

---

## Check Current User

```bash
whoami    # Display current username
```

---

## Execute a Command as Root

```bash
sudo apt update    # Run a command with root privileges
```

---

## Open a Root Shell

```bash
sudo -i    # Switch to root shell
```

Alternative:

```bash
sudo su    # Become root user
```

Exit root shell:

```bash
exit
```

---

## Check Sudo Permissions

```bash
sudo -l    # List commands allowed via sudo
```

This command is extremely important during Linux privilege escalation.

---

## Edit the Sudoers File

```bash
sudo visudo    # Safely edit sudo configuration
```

Never edit:

```bash
/etc/sudoers
```

directly with a text editor.

---

## Run Commands as Another User

```bash
sudo -u username command
```

Example:

```bash
sudo -u www-data whoami
```

---

## Preserve Environment Variables

```bash
sudo -E command
```

Useful when environment variables are required.

---

## Run Background Commands

```bash
sudo systemctl restart apache2
```

Restart a service with root privileges.

---

## View Sudo Logs

```bash
grep sudo /var/log/auth.log
```

Shows sudo activity on Debian-based systems.

---

## Common Administrative Commands

```bash
sudo apt update              # Update package lists
sudo apt upgrade             # Upgrade installed packages
sudo reboot                  # Restart system
sudo shutdown now            # Shut down immediately
sudo systemctl status ssh    # Check SSH service
```

---

## Sudo Misconfigurations

```bash
sudo -l                      # Enumerate sudo permissions
```

Look for:

- NOPASSWD entries
- Dangerous binaries
- Misconfigured scripts

These are frequently exploited during privilege escalation.

---

## Important Files

- `/etc/sudoers` → Main sudo configuration
- `/etc/sudoers.d/` → Additional sudo rules
- `/var/log/auth.log` → Authentication logs

---

## Key Takeaways

- `sudo` provides temporary root privileges.
- `sudo -l` is important for privilege escalation.
- Use `visudo` to edit sudo rules safely.
- Misconfigured sudo permissions can lead to full system compromise.