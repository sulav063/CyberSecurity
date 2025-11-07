**Antivirus**
Antivirus is security software that detects, blocks, and removes malicious software (malware) from a computer system.
- It uses different detection methods to identify and stop threats.
- Common features include:
  - Real-time protection
  - Automatic updates
  - Scheduled scans
  - Quarantine and removal
  - Threat reports
- Examples: Windows Defender, Avast, McAfee, Kaspersky, Norton, Bitdefender.

**Types of Detection Methods

**a. Signature-based Detection
- Detects malware by matching files against a database of known malware signatures.
- Effective for identifying **known threats** quickly.
- Requires frequent updates of the signature database.
- Limitation: Cannot detect new or unknown (zero-day) malware.

**b. Behaviour-based Detection
- Detects malware by monitoring the behaviour and actions of programs in real-time.
- Identifies suspicious activities like:
  - Unauthorized file modifications
  - Unusual network connections
  - Malicious process behaviour
- Effective for detecting **new, unknown, or polymorphic malware**.
- May produce false positives and can consume more system resources.
***
**EDR (Endpoint Detection and Response)

- EDR is an advanced security solution designed to monitor, detect, investigate, and respond to threats on endpoint devices.
- Provides continuous monitoring and data collection from endpoints.
- Helps identify and contain advanced threats, including zero-day attacks.
- Offers detailed forensics and root cause analysis for security incidents.
- Supports manual and automated response actions.

**Key Features
- Real-time endpoint activity monitoring
- Behavioral analysis and threat detection
- Threat hunting capabilities
- Incident investigation and root cause analysis
- Automated and manual response options

**Examples
- CrowdStrike Falcon
- SentinelOne
- Sophos Intercept X
- Microsoft Defender for Endpoint
- Carbon Black (VMware)
***
**XDR (Extended Detection and Response)
- XDR is an integrated security solution that collects and correlates data from multiple security layers — endpoints, network, cloud, email, and more.
- Provides unified visibility and centralized analysis across the entire IT environment.
- Enhances threat detection by correlating signals from different sources.
- Automates and coordinates responses across various security tools.
- Reduces detection and response time by offering a single pane of glass for security operations.
**Key Features
- Integration of multiple security products (endpoint, network, cloud, email)
- Cross-layer data correlation and analytics
- Centralized threat detection and response
- Automated workflows and incident response
- Enhanced threat hunting and investigation capabilities
**Examples
- Palo Alto Cortex XDR
- Microsoft Defender XDR
- Trend Micro XDR
- Sophos XDR
- Cisco XDR
***
**EDR VS XDR

| Feature          | EDR (Endpoint Detection and Response) | XDR (Extended Detection and Response)                         |
| ---------------- | ------------------------------------- | ------------------------------------------------------------- |
| **Scope**        | Focused on endpoint devices only      | Covers endpoints, networks, cloud, email, and more            |
| **Data Sources** | Endpoint data only                    | Multiple data sources (endpoint + other security layers)      |
| **Detection**    | Behavioral analysis on endpoints      | Cross-layer correlation for improved detection                |
| **Response**     | Response actions on endpoints         | Coordinated response across the entire environment            |
| **Visibility**   | Deep visibility into endpoints        | Unified, centralized visibility across all integrated sources |
| **Complexity**   | Endpoint-focused deployment           | Broader, integrated deployment across IT infrastructure       |
| **Examples**     | CrowdStrike Falcon, SentinelOne       | Palo Alto Cortex XDR, Microsoft Defender XDR                  |

