
A structured, step-by-step approach that ethical hackers use to assess the security of a system in a professional, legal, and controlled manner.

### 1. Reconnaissance (Information Gathering)
- **Goal:** Collect as much information as possible about the target.
- **Types:**
  - *Passive Reconnaissance:* No direct interaction (e.g., searching public records, WHOIS, social media).
  - *Active Reconnaissance:* Direct interaction with the target (e.g., ping sweeps, DNS queries).
- **Examples:** Identify IP addresses, domains, employee names, technologies used.

### 2. Scanning & Enumeration
- **Goal:** Identify live systems, open ports, services, and vulnerabilities.
- **Tools Used:** Nmap, Nessus, Netcat, Nikto, etc.
- **Activities:**
  - Port scanning
  - Service detection
  - OS fingerprinting
  - Vulnerability scanning
  - Enumerating users, shares, and network resources

### 3. Exploitation
- **Goal:** Use the discovered vulnerabilities to gain unauthorized access to the system.
- **Tools:** Metasploit, custom scripts, SQLmap, etc.
- **Focus Areas:** Buffer overflows, web application flaws, misconfigured services.

### 4. Privilege Escalation
- **Goal:** Move from limited access to higher (admin/root) privileges.
- **Types:**
  - *Vertical Escalation:* Gain higher privileges on the same system.
  - *Horizontal Escalation:* Access other users’ data or functions at the same privilege level.
- **Techniques:** Exploiting kernel flaws, weak permissions, misconfigured services.

### 5. Post-Exploitation
- **Goal:** Maintain access, gather deeper information, and understand the impact.
- **Activities:**
  - Planting backdoors or persistence mechanisms
  - Dumping credentials
  - Lateral movement to other systems
  - Collecting sensitive data (passwords, documents, databases)

### 6. Reporting
- **Goal:** Provide a clear, professional summary of the entire engagement.
- **Contents:**
  - Executive summary (non-technical overview)
  - Technical details of findings
  - Proof-of-concept (PoC) for each exploited vulnerability
  - Risk ratings and impact
  - Recommended mitigation and remediation steps

