
## Network Design

![[DHCP.png]]

| Device       | Interface | IP Address     | Network             |
|--------------|-----------|----------------|---------------------|
| Router0      | G0/0      | 192.168.10.1   | 192.168.10.0/24     |
| Router0      | G0/1      | 192.168.20.1   | 192.168.20.0/24     |
| Switch0      | –         | –              | Connected to PCs 0–3 |
| Switch1      | –         | –              | Connected to PCs 4–7 |
| PC0 – PC3    | DHCP      | 192.168.10.x   | Network 1           |
| PC4 – PC7    | DHCP      | 192.168.20.x   | Network 2           |

---

## Physical Connections

- Router G0/0 → Switch0  
- Router G0/1 → Switch1  
- PC0–PC3 → Switch0  
- PC4–PC7 → Switch1  

> 💡 Use **Copper Straight-through Cables** for all connections.

---

## Step-by-Step CLI Configuration (Router0)

```bash
enable
configure terminal

! Configure interface for Network 1
interface GigabitEthernet0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown
exit

! Configure interface for Network 2
interface GigabitEthernet0/1
 ip address 192.168.20.1 255.255.255.0
 no shutdown
exit

! Exclude router and reserved IPs from DHCP pool
ip dhcp excluded-address 192.168.10.1 192.168.10.10
ip dhcp excluded-address 192.168.20.1 192.168.20.10

! DHCP Pool for Network 1
ip dhcp pool NET1
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
exit

! DHCP Pool for Network 2
ip dhcp pool NET2
 network 192.168.20.0 255.255.255.0
 default-router 192.168.20.1
exit

end
write memory
```

---
## PC Configuration

On each PC:

1. Go to **Desktop > IP Configuration**
    
2. Select **DHCP**
    
3. Wait for the IP to be assigned automatically
    

- **PC0–PC3** should get IPs from **192.168.10.x**
    
- **PC4–PC7** should get IPs from **192.168.20.x**

---
## Testing

From **PC0**, open the command prompt and run:
`ping 192.168.10.1     # Router interface G0/0 ping 192.168.20.1     # Router interface G0/1 ping 192.168.20.11    # Ping PC from second network`

---
