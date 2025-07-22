  

### User Management

```bash

whoami                     # Current user

id                         # UID, GID, groups

adduser username           # Add new user

useradd username           # Add user (script-based)

passwd username            # Set/change password

deluser username           # Delete user

su - username              # Switch user

sudo -i                    # Root shell

```

  

### Permission Management

```bash

ls -l                      # Show ownership and permissions

chmod 664 file.txt         # rw-rw-r--

chmod 777 file.txt         # Full access

chmod 000 file.txt         # No access

chmod u+x file.txt         # Add execute for user

chmod u-x file.txt         # Remove execute for user

chmod o+w file.txt         # Add write for others

chmod -R 755 dir/          # Recursive permission change

```

  

### Ownership

```bash

chown root:root file.txt   # Set owner/group to root

chown kali:kali file.txt   # Set to kali

chown john:ldo file.txt    # Set owner to john, group to ldo

chown -R john:john folder/ # Recursive ownership change

```

  
---
