### 1. List all files and directories, including hidden ones  

```bash
ls -a
```

  

### 2. Check the current working directory  

```bash

pwd

```

  

### 3. Create a new directory named my_folder  

```bash

mkdir my_folder

```

  

### 4. Create an empty file named test.txt and add text  

```bash

touch test.txt

echo "This is a test file." > test.txt

```

  

### 5. Copy file1.txt to file2.txt  

```bash

echo "Original content of file1" > file1.txt

cp file1.txt file2.txt

```

  

### 6. Move or rename a file  

```bash

mv file2.txt renamed.txt

```

  

### 7. Remove a file and a directory  

```bash

rm test.txt

rm -r my_folder

```

  

### 8. View contents of a file  

```bash

cat view.txt

less view.txt

more view.txt

```

  

### 9. Search for the word "error" in log.txt  

```bash

grep "error" log.txt

```

  

### 10. Display first 10 and last 10 lines of a file  

```bash

head filename.txt

tail filename.txt

```

  

### 11. Find out the current logged-in user  

```bash

whoami

```

  

### 12. Change file permissions to allow only owner read/write  

```bash

chmod 600 filename.txt

```

  

### 13. Check disk space usage of all mounted filesystems  

```bash

df -h

```

  

### 14. Display running processes in real-time  

```bash

top

# or

htop

```

  

### 15. Kill a process by name or PID  

```bash

pkill process_name

kill PID

```

  

### 16. Schedule a one-time job using at or cron  

```bash

echo "bash /path/to/script.sh" | at 12:00

crontab -e

# Add this line for 12:00 daily:

0 12 * * * /path/to/script.sh

```

  

### 17. Make a script executable and run it  

```bash

chmod +x script.sh

./script.sh

```

  

### 18. Recursively change ownership of a directory and contents  

```bash

sudo chown -R user:group directory/

```

  

### 19. Search for files modified in the last 7 days  

```bash

find . -type f -mtime -7

```

  

### 20. Create a compressed tar archive of a directory  

```bash

tar -czvf archive.tar.gz directory/

```

  

### 21. Extract .tar.gz and .zip files  

```bash

tar -xzvf archive.tar.gz

unzip archive.zip

```

  

---

  

### 22. List open ports on your system  

```bash

sudo ss -tuln

# or

sudo netstat -tuln

```

  

### 23. Find location of an installed program (e.g., python3)  

```bash

which python3

whereis python3

command -v python3

```

  

### 24. Check memory and CPU usage  

```bash

free -h

top

vmstat

```

  

### 25. Redirect both stdout and stderr to a file  

```bash

your_command > output.log 2>&1

```

  

### 26. Create a user and set a password  

```bash

sudo adduser newuser

sudo passwd newuser

```

  

### 27. Safely add a user to sudoers file  

```bash

sudo visudo

# Add line:

newuser ALL=(ALL) NOPASSWD:ALL

```

  

### 28. Mount and unmount a USB drive manually  

```bash

lsblk

sudo mount /dev/sdX1 /mnt

sudo umount /mnt

```

  

### 29. Find your system’s IP address  

```bash

ip a

hostname -I

```

  

### 30. Change hostname temporarily and permanently  

```bash

sudo hostname newname

sudo hostnamectl set-hostname newname

```

  

### 31. Display and set environment variables  

```bash

printenv

echo $HOME

export MYVAR="hello"

```

  

### 32. Bash script to check if a service is running  

```bash

echo -e '#!/bin/bash

systemctl is-active --quiet apache2 && echo "Running" || echo "Not running"' > check_service.sh

chmod +x check_service.sh

./check_service.sh

```

  

### 33. Find and delete .log files larger than 100MB in /var/log  

```bash

sudo find /var/log -type f -name "*.log" -size +100M -exec rm -i {} \;

```

  

### 34. Check which users are logged in and from where  

```bash

who

w

```

  

### 35. Limit a user's disk usage using disk quotas  

```bash

# Edit /etc/fstab to add usrquota to partition

sudo mount -o remount /

sudo quotacheck -cum /

sudo quotaon /

sudo edquota username

```

