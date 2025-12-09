## HTTP
HTTP is a **stateless**, application-layer protocol used for transferring webpages and data between client and server.
### Stateless means:
- Every request is independent
- Server does not remember previous requests

Cookies and sessions solve this problem.

---
## Features of HTTP
- Human-readable
- Simple and flexible
- Works on port 80
- No encryption
- Uses request–response model
- Supports methods (GET, POST, etc.)
---
---
## HTTPS

HTTPS = HTTP + SSL/TLS encryption  
It ensures:
- Confidentiality (encrypted data)
- Integrity(no tampering)
- Authentication(server identity verified)
Works on port 443.

---
## SSL/TLS Certificate Components
Contains:
- Public key
- Domain name
- Certificate authority (CA)
- Validity dates
- Signature

Used to establish encrypted communication.

---


---
---
## Differences Between HTTP and HTTPS
|**S.No.**|**Parameter**|**HTTP**|**HTTPS**|
|---|---|---|---|
|**1**|Full Form|HyperText Transfer Protocol|HyperText Transfer Protocol Secure|
|**2**|Security Level|Not secure|Highly secure|
|**3**|Encryption|No encryption|Uses SSL/TLS encryption|
|**4**|Data Protection|Data sent as plain text|Data is encrypted before sending|
|**5**|Port Number|Uses Port **80**|Uses Port **443**|
|**6**|URL Format|`http://example.com`|`https://example.com`|
|**7**|SSL/TLS Certificate|Not required|Mandatory for secure connection|
|**8**|Vulnerability|Vulnerable to MITM, sniffing|Resistant to eavesdropping & MITM|
|**9**|Use Cases|Blogs, basic info sites|Banking, login pages, payments|
|**10**|Performance|Slightly faster (no encryption overhead)|Slightly slower (encryption overhead)|
|**11**|Authentication|No identity verification|Server identity verified via certificates|
|**12**|Data Integrity|Cannot ensure integrity|Ensures data is not modified in transit|
|**13**|SEO Ranking|Lower in SEO|Higher SEO ranking (Google prefers HTTPS)|
|**14**|Browser Display|Shows **Not Secure** in modern browsers|Shows **Padlock icon** 🔒 in browser|
|**15**|Trust Level|Lower user trust|High user trust|
|**16**|Cookie Security|Sends cookies without protection|Allows secure & HttpOnly cookies|
|**17**|Session Hijacking|Very high risk|Very low risk|
|**18**|Phishing Protection|Poor|Better security and reputation|
|**19**|Encryption Type|No encryption|Asymmetric + symmetric encryption|
|**20**|Certificate Authorities|Not used|Must be issued by CA (e.g., Let's Encrypt)|
|**21**|Cost|Free to use|SSL certificates may cost money (some free)|
|**22**|Data Visibility|Visible to hackers/sniffers|Encrypted; not readable to attackers|
|**23**|Use in API Communication|Not preferred|Standard for modern API security|
|**24**|Packet Inspection|Easy to inspect raw data|Difficult due to encryption|
|**25**|Man-in-the-middle Attacks|Easy target|Protected via encryption handshake|
|**26**|Suitable for Sensitive Data|Not suitable|Ideal for passwords, credit cards|
|**27**|Browser Warnings|Shows “Not Secure” for forms|No warning; secure connection|
|**28**|Handshake Requirement|No handshake|Requires SSL/TLS handshake|
|**29**|Encryption Algorithms|None|AES, RSA, SHA, ECC etc.|
|**30**|Redirect Rules|No automatic redirection|Often forces HTTPS-only|
|**31**|Use in Mobile Apps|Rarely used|Standard and recommended|
|**32**|Content Modification Risk|Data can be altered mid-route|Data cannot be altered|
|**33**|Usage Statistics|Declining|Dominant ( > 90% websites use HTTPS )|
|**34**|HTTP/2 Support|Limited|Fully supported|
|**35**|SSL Pinning|Not supported|Used in mobile security|
|**36**|Advanced Security Headers|Weak support|Full support (HSTS, CSP, HPKP)|
|**37**|Identity Verification|None|CA verifies site ownership|
|**38**|Connection Type|Unsecured TCP|Encrypted TLS over TCP|
|**39**|Government/Corporate Usage|Not allowed for sensitive use|Mandatory in corporates|
|**40**|Data Confidentiality|No confidentiality|Full confidentiality|