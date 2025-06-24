- **Desktop & Taskbar:**  
    The main workspace. The desktop holds icons, shortcuts, and files. The taskbar shows open programs, pinned apps, system tray icons, and notifications.
    
- **Start Menu:**  
    Central hub to access installed applications, recently used files, system settings, user account options, and power actions (restart, shutdown, sleep).
    
- **File Explorer:**  
    The default file manager for browsing, organizing, copying, moving, renaming, and deleting files and folders. Also provides quick access to drives, libraries, and network locations.
    
- **Control Panel:**  
    Legacy configuration hub for adjusting system settings like hardware, network, user accounts, installed programs, and security options.
    
- **Settings App:**  
    Modern, user-friendly interface for configuring Windows. Covers updates, privacy, devices, personalization, accounts, and system preferences.
    
- **Task Manager:**  
    Displays running applications, background processes, system resource usage (CPU, memory, disk, network), performance graphs, and startup program control.
    
- **Device Manager:**  
    Tool for viewing and managing hardware devices and drivers. Lets you update, disable, uninstall, or troubleshoot device drivers.
    
- **Task Scheduler:**  
    Allows scheduling and automating tasks or scripts to run at specified times or on certain triggers (like system startup or user logon).
    
- **Network and Sharing Center:**  
    View and manage network connections, configure adapter settings, set up new networks, and troubleshoot connectivity problems.
    
- **Services:**  
    Manages background services that run automatically or manually. Essential for system functions (e.g., Windows Update, Print Spooler). Misconfigured services can be abused in privilege escalation.
    
- **Registry Editor (regedit):**  
    Advanced tool for viewing and modifying the Windows Registry—a hierarchical database that stores system and application settings. Mistakes here can cause system instability.
    
- **Trusted Platform Module (TPM):**  
    A secure hardware chip used for storing cryptographic keys, enabling secure boot, and supporting features like BitLocker.
    
- **BitLocker:**  
    Built-in encryption tool that protects data on drives by encrypting the entire volume, often using TPM for secure key storage.
    
- **Command Prompt (CMD):**  
    Basic command-line interface for executing commands, running batch files, and troubleshooting.
    
- **PowerShell:**  
    Powerful command-line shell and scripting language designed for task automation and system management. Supports advanced scripts and remote administration.
    
- **Event Viewer:**  
    Logs system, security, and application events. Useful for diagnosing problems, monitoring suspicious activity, and conducting forensic investigations.
    
- **Windows Defender & Security Center:**  
    Integrated antivirus, anti-malware, firewall, and security status dashboard for protecting the system in real-time.
    

---

## User Accounts and Types

1. **Administrator Account**
    
    - Full system control.
        
    - Can install/uninstall software, change settings for all users, and manage other accounts.
        
2. **Standard User Account**
    
    - Limited permissions.
        
    - Can run applications and change own settings but cannot modify system-wide configurations.
        
3. **Guest Account**
    
    - Very limited access.
        
    - Intended for temporary users; usually disabled by default for security reasons.
        
4. **Built-in Accounts**
    
    - **Default Administrator:** Built-in superuser account; often disabled for security. Used for recovery and initial setup.
        
    - **Guest:** Built-in guest account; typically disabled to prevent unauthorized access.
        
    - **System Accounts:** Hidden accounts used by Windows services and processes (e.g., **Local System**, **Network Service**, **Local Service**).