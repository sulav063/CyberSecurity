Web applications work using the **client–server architecture**, where the browser acts as the **client** and the machine hosting the website is the **server**.

Here is the complete journey of a webpage from typing the address to loading on the screen:
### STEP 1: User enters a URL

Example:
https://www.amazon.com/products?category=mobiles

A URL consists of:

| Component         | Meaning             |
| ----------------- | ------------------- |
| https             | Protocol            |
| www.amazon.com    | Domain name         |
| /products         | Path                |
| ?category=mobiles | Query string        |
| #top              | Fragment (optional) |

---

### STEP 2: Browser checks local DNS cache

Your browser first looks in:
- Browser cache
- OS DNS cache
- Router cache
- ISP DNS cache

---

### STEP 3: DNS Lookup Occurs

If IP not found in cache, DNS translates domain → IP.
Example:
`amazon.com → 205.251.242.103`

### How DNS works:
- User → Resolver
- Resolver → Root Server
- Root → TLD Server (.com)
- TLD → Authoritative Server
- IP returned

---

### STEP 4: Browser opens TCP connection

Before sending a request, the browser sets up a connection using a **3-way handshake**:
1. SYN
2. SYN-ACK
3. ACK

If using HTTPS, it also performs:

### TLS Handshake

- Client Hello
- Server Hello
- Certificate exchange
- Encryption keys generated
- Secure connection established    

---

### STEP 5: Browser sends HTTP request
Example Request:
`GET /products HTTP/1.1 Host: amazon.com User-Agent: Chrome Accept: text/html`

---
### STEP 6: Server processes request

Server might:
- Execute PHP/Python/NodeJS code
- Query database
- Apply business logic
- Prepare HTML response
---

### STEP 7: Server sends HTTP response
Example:
`HTTP/1.1 200 OK Content-Type: text/html`

Then sends:
- HTML
- CSS
- JS
- Images
- API data

---

### STEP 8: Browser renders content
Rendering involves:
1. Parsing HTML
2. Building DOM
3. Loading CSS
4. Applying styles
5. Running JavaScript
6. Rendering graphics

---
