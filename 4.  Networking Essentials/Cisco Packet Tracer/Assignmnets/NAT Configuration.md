
![[NAT.png]]
## Step 1: Network Design & IP Plan

|Network|Subnet|Router Interface IP|Description|
|---|---|---|---|
|LAN1|192.168.10.0/29|192.168.10.1|Router0 LAN (PCs + DHCP)|
|LAN2|192.168.20.0/29|192.168.20.1|Router1 LAN (PCs + DHCP)|
|WAN Link|172.16.0.0/30|172.16.0.1 / 172.16.0.2|Router interconnection|
|Server0 subnet|192.168.30.0/29|192.168.30.1|Router0 Server subnet|
|Server1 subnet|192.168.40.0/29|192.168.40.1|Router1 Server subnet|

## Step 2: Device IP Addresses

|Device|Interface|IP Address|Subnet Mask|Notes|
|---|---|---|---|---|
|Router0|Gig0/0 (WAN)|172.16.0.1|255.255.255.252|Link to Router1|
|Router0|Gig0/1 (LAN1)|192.168.10.1|255.255.255.248|LAN1 DHCP & NAT inside|
|Router0|Gig0/2 (Server0)|192.168.30.1|255.255.255.248|NAT outside|
|Router1|Gig0/0 (WAN)|172.16.0.2|255.255.255.252|Link to Router0|
|Router1|Gig0/1 (LAN2)|192.168.20.1|255.255.255.248|LAN2 DHCP & NAT inside|
|Router1|Gig0/2 (Server1)|192.168.40.1|255.255.255.248|NAT outside|
|Server0|NIC|192.168.30.2|255.255.255.248|Static IP, gateway 192.168.30.1|
|Server1|NIC|192.168.40.2|255.255.255.248|Static IP, gateway 192.168.40.1|
|PC0, PC1|NIC|DHCP (192.168.10.2–6)|255.255.255.248|LAN1 PCs|
|PC2, PC3|NIC|DHCP (192.168.20.2–6)|255.255.255.248|LAN2 PCs|

## Step 3: Router0 Configuration

```
enable
configure terminal

! Configure WAN interface
interface gigabitEthernet0/0
 ip address 172.16.0.1 255.255.255.252
 no shutdown
exit

! Configure LAN1 interface (NAT inside)
interface gigabitEthernet0/1
 ip address 192.168.10.1 255.255.255.248
 ip nat inside
 no shutdown
exit

! Configure Server0 interface (NAT outside)
interface gigabitEthernet0/2
 ip address 192.168.30.1 255.255.255.248
 ip nat outside
 no shutdown
exit

! DHCP Configuration for LAN1
ip dhcp excluded-address 192.168.10.1
ip dhcp pool LAN1
 network 192.168.10.0 255.255.255.248
 default-router 192.168.10.1
 dns-server 8.8.8.8
exit

! Static NAT for Server0 (public IP: 203.0.113.10)
ip nat inside source static 192.168.30.2 203.0.113.10

! Dynamic NAT for LAN1 PCs
access-list 1 permit 192.168.10.0 0.0.0.7
ip nat inside source list 1 interface gigabitEthernet0/2 overload

! Static Routes for LAN2 and Server1 subnet via Router1 WAN IP
ip route 192.168.20.0 255.255.255.248 172.16.0.2
ip route 192.168.40.0 255.255.255.248 172.16.0.2

end
```

## Step 4: Router1 Configuration

```
enable
configure terminal

! Configure WAN interface
interface gigabitEthernet0/0
 ip address 172.16.0.2 255.255.255.252
 no shutdown
exit

! Configure LAN2 interface (NAT inside)
interface gigabitEthernet0/1
 ip address 192.168.20.1 255.255.255.248
 ip nat inside
 no shutdown
exit

! Configure Server1 interface (NAT outside)
interface gigabitEthernet0/2
 ip address 192.168.40.1 255.255.255.248
 ip nat outside
 no shutdown
exit

! DHCP Configuration for LAN2
ip dhcp excluded-address 192.168.20.1
ip dhcp pool LAN2
 network 192.168.20.0 255.255.255.248
 default-router 192.168.20.1
 dns-server 8.8.8.8
exit

! Static NAT for Server1 (public IP: 203.0.113.20)
ip nat inside source static 192.168.40.2 203.0.113.20

! Dynamic NAT for LAN2 PCs
access-list 1 permit 192.168.20.0 0.0.0.7
ip nat inside source list 1 interface gigabitEthernet0/2 overload

! Static Routes for LAN1 and Server0 subnet via Router0 WAN IP
ip route 192.168.10.0 255.255.255.248 172.16.0.1
ip route 192.168.30.0 255.255.255.248 172.16.0.1

end
```

## Step 5: PC and Server IP Setup

|Device|IP Address|Subnet Mask|Default Gateway|Notes|
|---|---|---|---|---|
|PC0, PC1|DHCP from Router0|255.255.255.248|192.168.10.1|LAN1|
|PC2, PC3|DHCP from Router1|255.255.255.248|192.168.20.1|LAN2|
|Server0|192.168.30.2|255.255.255.248|192.168.30.1|Static IP|
|Server1|192.168.40.2|255.255.255.248|192.168.40.1|Static IP|

## Step 6: Verify the Configuration

### On Routers:

```
show ip nat translations
show ip nat statistics
show ip route
```

### On PCs/Servers:

```
ping <IP of device on other LAN or public IP>
ping 203.0.113.10    ! Server0 public NAT IP
ping 203.0.113.20    ! Server1 public NAT IP
```