# Static Routing with DHCP – Full Configuration

## 1. Subnetting Plan

| Subnet        | Network Address | Subnet Mask         | Interface        | Router     |
|---------------|------------------|----------------------|------------------|------------|
| LAN1          | 50.0.0.0         | 255.255.255.0 (/24)  | G0/1             | R1 (Kathmandu) |
| LAN2          | 60.0.0.0         | 255.255.255.0 (/24)  | G0/2             | R1 (Kathmandu) |
| LAN3          | 70.0.0.0         | 255.255.255.0 (/24)  | G0/1             | R2 (Pokhara)   |
| LAN4          | 80.0.0.0         | 255.255.255.0 (/24)  | G0/2             | R2 (Pokhara)   |
| Link (R1–R2)  | 100.0.0.0        | 255.255.255.252 (/30)| G0/0 <-> G0/0    | R1 <-> R2  |

## 2. Router R1 (Kathmandu) Configuration

```bash
enable
configure terminal

! Interface for LAN1
interface gigabitEthernet 0/1
ip address 50.0.0.1 255.255.255.0
no shutdown
exit

! Interface for LAN2
interface gigabitEthernet 0/2
ip address 60.0.0.1 255.255.255.0
no shutdown
exit

! Interface to R2
interface gigabitEthernet 0/0
ip address 100.0.0.1 255.255.255.252
no shutdown
exit

! DHCP for LAN1
ip dhcp excluded-address 50.0.0.1
ip dhcp pool LAN1
network 50.0.0.0 255.255.255.0
default-router 50.0.0.1
dns-server 8.8.8.8
exit

! DHCP for LAN2
ip dhcp excluded-address 60.0.0.1
ip dhcp pool LAN2
network 60.0.0.0 255.255.255.0
default-router 60.0.0.1
dns-server 8.8.8.8
exit

! Static Routes to Pokhara LANs
ip route 70.0.0.0 255.255.255.0 100.0.0.2
ip route 80.0.0.0 255.255.255.0 100.0.0.2

end
```

## 3. Router R2 (Pokhara) Configuration

```bash
enable
configure terminal

! Interface to R1
interface gigabitEthernet 0/0
ip address 100.0.0.2 255.255.255.252
no shutdown
exit

! Interface for LAN3
interface gigabitEthernet 0/1
ip address 70.0.0.1 255.255.255.0
no shutdown
exit

! Interface for LAN4
interface gigabitEthernet 0/2
ip address 80.0.0.1 255.255.255.0
no shutdown
exit

! DHCP for LAN3
ip dhcp excluded-address 70.0.0.1
ip dhcp pool LAN3
network 70.0.0.0 255.255.255.0
default-router 70.0.0.1
dns-server 8.8.8.8
exit

! DHCP for LAN4
ip dhcp excluded-address 80.0.0.1
ip dhcp pool LAN4
network 80.0.0.0 255.255.255.0
default-router 80.0.0.1
dns-server 8.8.8.8
exit

! Static Routes to Kathmandu LANs
ip route 50.0.0.0 255.255.255.0 100.0.0.1
ip route 60.0.0.0 255.255.255.0 100.0.0.1

end
```
