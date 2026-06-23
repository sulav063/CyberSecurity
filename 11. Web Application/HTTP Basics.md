# HTTP Basics

## Overview

HTTP (HyperText Transfer Protocol) is the protocol used for communication between clients and web servers.

HTTPS is the secure version of HTTP and uses TLS encryption.

---

## Common Ports

- HTTP → 80
- HTTPS → 443

---

## Request Structure

```text
Method URI Version
Headers
Body
```

Example:

```text
GET /index.html HTTP/1.1
Host: example.com
```

---

## Response Structure

```text
Version Status-Code
Headers
Body
```

Example:

```text
HTTP/1.1 200 OK
```

---

## View a Website

```bash
curl https://example.com
```

Retrieve webpage contents.