
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