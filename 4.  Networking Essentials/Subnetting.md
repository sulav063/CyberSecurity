
**Subnetting** is the process of dividing a larger IP network into smaller, more efficient **sub-networks (subnets)**. This improves performance, security, and address management.

---

### Why Subnet?

- **Efficient IP allocation** – Avoids wasting IP addresses.
- **Improved network performance** – Limits broadcast domains.
- **Better security** – Isolates departments or teams.[[]()]()
- **Simpler management** – Easier to troubleshoot and scale.

---

## Key Concepts

### 1. **Subnet Mask**
- Used to define the boundary between the **network** and **host** portion of an IP address.
- Example:  
  `255.255.255.0` → The first 24 bits are the network, last 8 bits are for hosts.

### 2. **CIDR Notation** (Classless Inter-Domain Routing)
- Shorthand for subnet mask using a slash `/` and the number of bits used for the network.
- Example:  
  `/24` = `255.255.255.0` = 24 bits for network, 8 for host

---

## Subnet Mask Conversion Table

| CIDR | Subnet Mask        | Binary Representation                  | # of Hosts |
|------|--------------------|-----------------------------------------|------------|
| /8   | 255.0.0.0          | 11111111.00000000.00000000.00000000     | 16,777,214 |
| /16  | 255.255.0.0        | 11111111.11111111.00000000.00000000     | 65,534     |
| /24  | 255.255.255.0      | 11111111.11111111.11111111.00000000     | 254        |
| /25  | 255.255.255.128    | 11111111.11111111.11111111.10000000     | 126        |
| /26  | 255.255.255.192    | 11111111.11111111.11111111.11000000     | 62         |
| /27  | 255.255.255.224    | 11111111.11111111.11111111.11100000     | 30         |
Number of usable hosts = 2ⁿ - 2 (where n is the number of host bits)

---
# IP Address Classes (Classful Addressing)

| Class   | Leading Bits | Starting Octet Range | IP Address Range            | Default Subnet Mask | Network ID Bits      | Host ID Bits | No. of Networks | Addresses per Network | Hosts per Network | Usage                           |
| ------- | ------------ | -------------------- | --------------------------- | ------------------- | -------------------- | ------------ | --------------- | --------------------- | ----------------- | ------------------------------- |
| Class A | 0            | 0 – 127              | 0.0.0.0 – 127.255.255.255   | 255.0.0.0 (/8)      | 8 bits (1st octet)   | 24 bits      | 2⁷ = 128        | 2²⁴ = 16,777,216      | ~16 million       | Large organizations, ISPs       |
| Class B | 10           | 128 – 191            | 128.0.0.0 – 191.255.255.255 | 255.255.0.0 (/16)   | 16 bits (1st+2nd)    | 16 bits      | 2¹⁴ = 16,384    | 2¹⁶ = 65,536          | ~65,000           | Medium-sized networks           |
| Class C | 110          | 192 – 223            | 192.0.0.0 – 223.255.255.255 | 255.255.255.0 (/24) | 24 bits (1–3 octets) | 8 bits       | 2²¹ = 2,097,152 | 2⁸ = 256              | 254               | Small networks (LANs)           |
| Class D | 1110         | 224 – 239            | 224.0.0.0 – 239.255.255.255 | —                   | Not defined          | Not defined  | Not defined     | Not defined           | —                 | Multicast (group communication) |
| Class E | 1111         | 240 – 255            | 240.0.0.0 – 255.255.255.255 | —                   | Not defined          | Not defined  | Not defined     | Not defined           | —                 | Experimental/Reserved           |
> ⚠️ Notes:
> - **Network ID** identifies the subnet or network.
> - **Host ID** identifies individual devices on that network.
> - `127.x.x.x` is **reserved for loopback testing** (localhost) and cannot be assigned to hosts.
> - Classes **D** and **E** are **not used for regular device addressing**.
---
# IP Address Class Structure (Net ID vs Host ID)

This diagram shows how the **32-bit IPv4 address** is divided between **Network ID** and **Host ID** in different classes.
# IP Address Class Structure (Net ID vs Host ID)

This diagram shows how the **32-bit IPv4 address** is divided between **Network ID** and **Host ID** in different classes.

| Class   | Byte 1       | Byte 2       | Byte 3       | Byte 4       | Description                           | Default Subnet Mask |
|---------|--------------|--------------|--------------|--------------|----------------------------------------|----------------------|
| Class A | NET ID       | HOST ID      | HOST ID      | HOST ID      | First 8 bits → Network; 24 → Host      | 255.0.0.0 (/8)       |
| Class B | NET ID       | NET ID       | HOST ID      | HOST ID      | First 16 bits → Network; 16 → Host     | 255.255.0.0 (/16)    |
| Class C | NET ID       | NET ID       | NET ID       | HOST ID      | First 24 bits → Network; 8 → Host      | 255.255.255.0 (/24)  |
| Class D | MULTICAST ADDRESS (Not split)               | Used for multicast addressing         | —                    |
| Class E | RESERVED (Not split)                        | Reserved for research/experimental use| —                    |

> ✅ Byte = 8 bits  
> ✅ Total IPv4 length = 4 Bytes = 32 bits  
> ✅ Class A is suitable for large networks, C for smaller ones  
> ✅ Class D is used for multicast, not for host assignment  
> ✅ Class E is reserved for future or experimental purposes


---
## Conversion Example

### Convert Subnet Mask: `255.255.255.192`

1. Write each octet in binary:
   - 255 = `11111111`
   - 255 = `11111111`
   - 255 = `11111111`
   - 192 = `11000000`

   👉 Binary: `11111111.11111111.11111111.11000000`

2. Count number of 1s: 26 → **CIDR = /26**

3. Host bits = 6 → Usable Hosts = 2⁶ - 2 = **62 hosts**

---

