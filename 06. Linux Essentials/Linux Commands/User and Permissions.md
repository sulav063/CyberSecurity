### Basic User Management
```bash
whoami              # Check current username
id                  # Display user and group IDs
adduser user_name   # Add a new user with setup
useradd user_name   # Add a new user (basic)
deluser user_name   # Remove a user account
usermod -aG group user # Add user to a group
```

****
### Permission Management
```bash
chmod 664 file.txt  # Set permissions: rw for owner/group, r for others
chmod -R 755 dir    # Recursively set permissions
chmod u+x file.txt  # Add execute permission for user
chmod o-w file.txt  # Remove write permission for others
chown user file.txt # Change file owner
chown -R user dir   # Recursively change ownership
chgrp group file.txt # Change group ownership
getfacl file.txt    # Display ACL permissions
setfacl -m u:user:rw file.txt # Set ACL for a specific user
```

****
### Switching Users
```bash
su -l               # Switch to root with login shell
su user_name        # Switch to specified user
sudo -i             # Switch to root environment
sudo -u user cmd    # Run command as specified user
```