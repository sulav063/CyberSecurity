# Penetration Testing

Penetration Testing (Pentesting) is a simulated, authorized cyberattack used to identify and exploit security weaknesses in systems, networks, or applications.

Its purpose is to assess how well an organization can defend against real attacks and to find vulnerabilities before malicious hackers do.

Penetration tests are performed by ethical hackers using both manual and automated tools.

---

## Domains of Penetration Testing

### 1. Application Penetration Testing
Focuses on finding vulnerabilities in software applications (web, mobile, desktop).

**Types:**
- Web Application Testing (e.g., SQL injection, XSS, CSRF)
- Mobile Application Testing (e.g., insecure storage, reverse engineering)
- Desktop/Client-Side App Testing (e.g., DLL injection, buffer overflow)

### 2. Network Penetration Testing
Evaluates the security of network infrastructure and connected devices.

**Types:**
- External Network Testing (from outside the organization)
- Internal Network Testing (simulating an insider threat)
- Wireless Network Testing (Wi-Fi security, rogue APs)

### 3. API Penetration Testing
Tests APIs (Application Programming Interfaces) used in apps or services. Checks for:
- Improper authentication
- Rate-limiting issues
- Insecure data handling
- Injection flaws

### 4. Wireless Penetration Testing
Focuses on wireless technologies (Wi-Fi, Bluetooth, Zigbee). Identifies:
- Misconfigurations
- Weak encryption (WEP/WPA)
- Rogue access points

### 5. IoT (Internet of Things) Penetration Testing
Tests smart and connected devices like smart TVs, wearables, and home automation systems. Includes:
- Firmware analysis
- Insecure communication
- Physical port testing

### 6. Cloud Penetration Testing
Assesses the security of cloud platforms and services (e.g., AWS, Azure, GCP).

**Focus areas:**
- Misconfigured storage (e.g., open S3 buckets)
- Insecure IAM policies
- API gateway flaws
- Exposed credentials or secrets

### 7. OT / ICS / SCADA Penetration Testing
Focuses on industrial control systems used in critical infrastructure.

**Types:**
- ICS (Industrial Control Systems)
- SCADA (Supervisory Control and Data Acquisition)
- PLC (Programmable Logic Controller) Testing

Checks protocol vulnerabilities, physical security gaps, and poor network segmentation.

### 8. Automobile Penetration Testing
Evaluates the cybersecurity of connected vehicles.

**Key areas:**
- Infotainment systems
- CAN bus exploitation
- Remote keyless entry attacks
- Firmware and telematics vulnerabilities

---

## CTF – Capture The Flag

- CTF (Capture The Flag) games involve vulnerable machines with hidden flags.
- Players must find and exploit vulnerabilities to capture these flags.

---

## Bug Bounty

- Organizations expose their systems to ethical hackers to identify security flaws.
- If a reported bug is valid, the finder receives a reward (cash, gifts, merchandise, or a Hall of Fame mention).

---

## Key Terminologies (Detailed)

### Vulnerability
A flaw or weakness in a system that can be exploited by an attacker to gain unauthorized access or perform malicious actions. Vulnerabilities may exist in software, hardware, configurations, or human processes.

### Threat
A potential cause of an unwanted incident that may result in harm to a system or organization. It represents a possible danger, such as a hacker, malware, or natural disaster.

### Host, End-Device, Endpoints
Devices connected to a network that communicate or process data. These include desktops, laptops, smartphones, servers, and IoT devices. Endpoints are often targets in attacks because they interact directly with users.

### Exploit
A program or script designed to take advantage of a vulnerability. Exploits can lead to actions like gaining unauthorized access, stealing data, or executing arbitrary code.

### Payload
The component of malware or an exploit that carries out the intended malicious action. It could be a virus, ransomware encryption routine, backdoor, or system command.

### Malware
Malicious software designed to harm, exploit, or otherwise compromise a system. Categories of malware include:
- Virus: Replicates by infecting files
- Worm: Spreads without human interaction
- Trojan: Disguises itself as legitimate software
- Spyware: Monitors user activity
- Ransomware: Encrypts data and demands payment

### Social Engineering
Manipulative techniques used to trick individuals into revealing confidential information or performing actions that compromise security. Common tactics include phishing emails, impersonation, and baiting.

---

## Security Tools and Concepts (Detailed)

### Antivirus
A security application designed to detect, prevent, and remove malicious software. Antivirus programs monitor system activity, scan files and emails, and provide real-time protection. Popular examples include McAfee, Windows Defender, Avast, and Quick Heal.

### EDR (Endpoint Detection and Response)
A security solution that provides continuous monitoring and response to threats on endpoints. EDR tools collect data, analyze behavior, and help security teams detect and respond to sophisticated attacks.

### MDR (Managed Detection and Response)
An outsourced security service that provides threat detection and response capabilities. MDR combines EDR with human expertise, allowing organizations to monitor, analyze, and remediate threats 24/7 without managing the tools internally.

### XDR (Extended Detection and Response)
An advanced threat detection approach that unifies data from multiple security layers (endpoints, servers, emails, cloud workloads) to provide broader visibility and coordinated threat response across the organization.

### DLP (Data Loss Prevention)
A technology that monitors and controls the transfer of sensitive information to prevent unauthorized access or data breaches. DLP tools inspect data in motion (e.g., network traffic), data at rest (e.g., databases), and data in use (e.g., open files) to ensure sensitive information is not leaked.

---

