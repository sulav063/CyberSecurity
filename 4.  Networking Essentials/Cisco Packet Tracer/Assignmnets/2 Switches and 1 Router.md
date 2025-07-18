# Network Setup: 8 PCs via 2 Switches and 1 Router with Subnetting

---
![[2 switch 1 router.png]]
## Devices

- PCs: PC0 to PC7
    
- Switches: Switch0, Switch1
    
- Router: Router0
    
- Cables: Copper straight-through cables
    

---

## Subnetting Details

|Subnet|Network Address|Host Range|Broadcast Address|
|---|---|---|---|
|A|192.168.0.0/25|192.168.0.1 – 192.168.0.126|192.168.0.127|
|B|192.168.0.128/25|192.168.0.129 – 192.168.0.254|192.168.0.255|

---

## IP Address Assignments

### Subnet A (Switch0 Side)

|Device|IP Address|Subnet Mask|Default Gateway|
|---|---|---|---|
|PC0|192.168.0.10|255.255.255.128|192.168.0.1|
|PC1|192.168.0.11|255.255.255.128|192.168.0.1|
|PC2|192.168.0.12|255.255.255.128|192.168.0.1|
|PC3|192.168.0.13|255.255.255.128|192.168.0.1|

### Subnet B (Switch1 Side)

|Device|IP Address|Subnet Mask|Default Gateway|
|---|---|---|---|
|PC4|192.168.0.130|255.255.255.128|192.168.0.129|
|PC5|192.168.0.131|255.255.255.128|192.168.0.129|
|PC6|192.168.0.132|255.255.255.128|192.168.0.129|
|PC7|192.168.0.133|255.255.255.128|192.168.0.129|

---

## Router Interfaces

|Interface|IP Address|Subnet Mask|Subnet|
|---|---|---|---|
|GigabitEthernet0/0|192.168.0.1|255.255.255.128|192.168.0.0/25|
|GigabitEthernet0/1|192.168.0.129|255.255.255.128|192.168.0.128/25|

---

## Physical Connections

- PC0, PC1, PC2, PC3 → Switch0 (Ports Fa0/1 – Fa0/4)
    
- PC4, PC5, PC6, PC7 → Switch1 (Ports Fa0/1 – Fa0/4)
    
- Switch0 → Router0 GigabitEthernet0/0
    
- Switch1 → Router0 GigabitEthernet0/1
    

---
## Router0 CLI Configuration

enable 
configure terminal  
interface gigabitEthernet0/0 
ip address 192.168.0.1 255.255.255.128  
no shutdown 
exit  

interface gigabitEthernet0/1  
ip address 192.168.0.129 255.255.255.128 
no shutdown 
exit  
exit 
write memory`

---
## Connectivity Testing (Ping Commands)

### Test within same subnet

From PC0:
`ping 192.168.0.11  # PC1 in subnet A`

From PC4:
`ping 192.168.0.131  # PC5 in subnet B`

### Test across subnets (via router)

From PC0:

`ping 192.168.0.130  # PC4 in subnet B`

From PC7:
`ping 192.168.0.12   # PC2 in subnet A`