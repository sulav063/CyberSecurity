dont ne### Viewing Processes

```bash
ps                         # Show current user's processes
ps -A                      # Show all processes
ps -e | more               # All processes with pagination
ps aux                     # Detailed view of all running processes
ps aux | more              # Detailed + paginated view
ps -ef                     # Full-format listing of all processes
ps -u root                 # Processes run by 'root' user
ps -ejH                    # Show all processes in a tree (hierarchy)
watch ps -e                # Continuously monitor processes
```

---
### Searching and Filtering Processes
```bash
ps aux | grep apache2      # Search for apache2 process
ps -e | grep apache2       # Another way to find apache2
ps -ejH | grep apache2     # Tree view filtered for apache2
ps -ejf | grep apache2     # Full-format tree view filtered for apache2
pgrep apache2              # Get PID(s) for apache2
pidof apache2              # Alternative PID fetcher
```

---
### Killing or Stopping Processes

```bash
kill <PID>                 # Gracefully kill a process
kill -9 <PID>              # Force kill a process
sudo kill -9 <PID>         # Force kill with superuser rights
sudo kill -15 <PID>        # Gracefully terminate with sudo
killall apache2            # Kill all processes named apache2
fuser -k 80/tcp            # Kill process using port 80
```

---
### Managing Services (systemctl)
```bash
systemctl start apache2    # Start apache2 service
systemctl stop apache2     # Stop apache2 service
systemctl status apache2   # Check apache2 status
systemctl restart apache2  # Restart apache2 service
```

---
### Monitoring System Activity
```bash
top                        # Live system monitor
htop                       # Enhanced top (if installed)
```

---
### Process + Port/File Interaction
```bash
lsof                       # List open files
lsof -i :80                # List process using port 80
```
---

## Add and Mount a New Hard Disk in VMware (Step-by-Step)

####  Step 1: Add a New Virtual Hard Disk in VMware Workstation

1. Shut down your Kali Linux VM.
2. In VMware Workstation, right-click your Kali VM → choose **Settings**.
3. Click **Add...**
4. Select **Hard Disk** → Click **Next**.
5. Choose **SCSI (recommended)** → Click **Next**.
6. Select **Create a new virtual disk** → Click **Next**.
7. Set size (e.g., 40 GB), check "**Store as a single file**" → Click **Next**.
8. Click **Finish**, then **OK**.
9. Start your Kali Linux VM.
#### 💻 Step 2: Inside Kali Linux — Run These Commands

```bash
# 1️⃣ View all disks to detect the new one (usually /dev/sdb)
lsblk

# 2️⃣ Partition the new disk
sudo fdisk /dev/<secondary_storage>

# 👉 Inside fdisk, follow these steps:
n       # new partition  
p       # primary  
1       # partition number  
<Enter> # accept default first sector  
<Enter> # accept default last sector  
w       # write changes and exit
```


```bash
# 3️⃣ Format the new partition
sudo mkfs.ext4 /dev/<secondary_storage>1

# 4️⃣ Check existing mount points
sudo ls /mnt

# 5️⃣ Create a mount point
sudo mkdir /mnt/<directory_name>

# 6️⃣ Mount the formatted partition
sudo mount /dev/<secondary_storage>1 /mnt/<directory_name>

# 7️⃣ Confirm it is mounted
lsblk
```

### Example with Actual Names
```bash
lsblk
sudo fdisk /dev/sdb        # Use steps: n → p → 1 → Enter → Enter → w
sudo mkfs.ext4 /dev/sdb1
sudo mkdir /mnt/data
sudo mount /dev/sdb1 /mnt/data
lsblk

```