
---

## Linux Architecture

Linux is a **modular, layered operating system** that interacts with hardware and software using well-defined components. It follows a **monolithic kernel** design.

![[Linux Architcture.png]]

### Key Components:

---

### 1. Hardware
- Physical components: CPU, RAM, storage, network devices, etc.
- Kernel directly communicates with hardware via device drivers.

---

### 2. Kernel
- The **core** of Linux — manages all low-level tasks.
- Responsibilities include:
  - **Process management** (scheduling, multitasking)
  - **Memory management** (allocation, paging)
  - **Device management** (via drivers)
  - **File system access**
  - **Networking stack**
- Linux uses a **monolithic kernel**, which means all kernel services run in kernel space.

---

### 3. System Libraries
- Special functions/programs that allow applications to interact with the kernel.
- Example: GNU C Library (`glibc`) provides standard API calls (e.g., `printf`, `open`).

---

### 4. Shell (Command Interpreter)
- Accepts user commands and passes them to the kernel for execution.
- Examples: `bash`, `zsh`, `sh`, `fish`
- Can be CLI or GUI-based (Terminal Emulator or Desktop Environment).

---

### 5. Applications
- End-user software: browsers, editors, compilers, etc.
- Runs in user space and uses libraries to interact with the kernel.

---

### Diagram (Text-Based Overview):

+---------------------------+
|   Applications (User)         |
+---------------------------+
|   Shell / GUI Interface       |
+---------------------------+
|   System Libraries             |
+---------------------------+
|   Linux Kernel                   |
+---------------------------+
|   Hardware                       |
+---------------------------+

---
## Linux Directory Structure

![[Linux Directory Structure.png]]

Linux follows a **hierarchical directory structure**, with the **root (`/`) directory** at the top. Every file or directory stems from `/`.

### Standard Directories:
|Directory|Description|
|---|---|
|`/`|Root of the filesystem|
|`/bin`|Essential binary commands (`ls`, `cp`, `rm`)|
|`/boot`|Boot loader files and Linux kernel|
|`/dev`|Device files (e.g., `/dev/sda` for hard disks)|
|`/etc`|System-wide configuration files|
|`/home`|User home directories (e.g., `/home/student`)|
|`/lib`|Libraries required by programs in `/bin` and `/sbin`|
|`/media`|Mount point for removable media (USB/CD)|
|`/mnt`|Temporary mount point for manual mounting|
|`/opt`|Optional software packages|
|`/proc`|Virtual filesystem with system and process info|
|`/root`|Home directory for the root user|
|`/run`|Runtime information (e.g., process IDs)|
|`/sbin`|System binaries (used by root)|
|`/srv`|Service-related data (e.g., web, FTP)|
|`/tmp`|Temporary files (cleared on reboot)|
|`/usr`|User programs, libraries, documentation|
|`/var`|Variable files: logs, spools, cache|
