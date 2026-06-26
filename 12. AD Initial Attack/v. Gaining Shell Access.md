
## Overview

A **shell** provides a command-line interface that allows users to interact with an operating system. System administrators use shells for managing systems, while security professionals study shell access as part of understanding post-exploitation and system administration.

After an attacker successfully exploits a vulnerability, obtaining shell access is often described in cybersecurity courses as the point where they can interact directly with the compromised system. Defenders study this concept to understand how to detect and prevent unauthorized access.

---

## Types of Shells

### Command Shell

Allows users to execute operating system commands.

Examples include:

- Windows Command Prompt (CMD)
    
- Windows PowerShell
    
- Linux Bash
    
- Zsh
    

---

### Interactive Shell

An interactive shell allows users to enter commands one at a time and immediately view the output.

---

### Non-Interactive Shell

Commands are executed automatically through scripts without requiring user interaction.

---

## Legitimate Uses

System administrators use shells to:

- Manage users
    
- Configure services
    
- Install software
    
- Monitor processes
    
- Troubleshoot systems
    
- Automate repetitive tasks
    

---

## Why Shell Access Matters

Because a shell provides direct access to operating system functions, protecting shell access is essential for maintaining system security.

Organizations should ensure that only authorized users can access administrative shells.

---

## Security Considerations

Administrators should:

- Use strong passwords.
    
- Enable multi-factor authentication.
    
- Restrict administrative privileges.
    
- Monitor login attempts.
    
- Keep systems updated.
    
- Review audit logs regularly.
    

---

## Detection

Signs of suspicious shell activity may include:

- Unexpected remote logins
    
- Unknown administrator accounts
    
- Unusual process execution
    
- Suspicious command histories
    
- Unexpected network connections
    

Monitoring tools such as Windows Event Viewer, Sysmon, and SIEM platforms can help detect abnormal activity.

---

## Importance in Cybersecurity

Understanding shell access helps students learn:

- Operating system administration
    
- Privilege management
    
- Access control
    
- Incident response
    
- Defensive monitoring
    

This knowledge is valuable for both system administrators and cybersecurity professionals.

---

# Basic Shell Commands

Shell commands are used to interact with the operating system through a command-line interface (CLI). They allow users to navigate directories, inspect system information, manage files, monitor system resources, and perform administrative tasks. These commands are fundamental for Linux system administration, cybersecurity, and troubleshooting.

---

# Basic Shell Commands (Linux)

## Display Current User

```bash
whoami
```

Displays the username of the currently logged-in user.

---

## Display Current Directory

```bash
pwd
```

Prints the absolute path of the current working directory.

---

## List Files

```bash
ls -la
```

Lists all files and directories, including hidden files, along with detailed information such as permissions, owner, size, and modification date.

---

## Display System Information

```bash
uname -a
```

Displays detailed information about the operating system, Linux kernel version, architecture, and hostname.

---

## Display Hostname

```bash
hostname
```

Displays the hostname (computer name) of the current system.

---

## Display Running Processes

```bash
ps aux
```

Lists all currently running processes along with their process ID (PID), CPU usage, memory usage, and owner.

---

## Display Logged-in Users

```bash
who
```

Shows all users who are currently logged into the system, including their login terminals and login times.

---

## Display Disk Usage

```bash
df -h
```

Displays the available and used disk space on mounted file systems in a human-readable format.

---

## Display Memory Usage

```bash
free -h
```

Displays information about RAM and swap memory usage in a human-readable format.

---

## Display Network Interfaces

```bash
ip addr
```

Displays all configured network interfaces along with their IPv4 and IPv6 addresses.

---

## Display Listening Ports

```bash
ss -tuln
```

Displays all listening TCP and UDP ports currently open on the system.

---

# Windows Shell Commands

The following commands can be executed in **Command Prompt (CMD)** or **PowerShell** to retrieve system and network information.

---

## Display Current User

```bash
whoami
```

Displays the username of the currently logged-in Windows user.

---

## Display Computer Name

```bash
hostname
```

Displays the hostname (computer name) of the Windows system.

---

## Display Current Directory

```bash
pwd
```

Prints the current working directory in PowerShell.

---

## List Files and Folders

```bash
Get-ChildItem
```

Lists all files and folders in the current directory. This command is equivalent to the Linux `ls` command.

---

## Display Running Processes

```bash
Get-Process
```

Displays all currently running processes, including their process IDs (PID), CPU usage, and memory consumption.

---

## Display Network Configuration

```bash
ipconfig /all
```

Displays detailed information about all network adapters, including IPv4 addresses, IPv6 addresses, DNS servers, MAC addresses, and gateway information.

---

## Display Active Network Connections

```bash
netstat -ano
```

Displays all active network connections, listening ports, process IDs (PID), and connection states.

---

