### Design a network for an organization where 3 departments are present each department has 8 employees and all of them will have dynamic IP addresses Network range is 10.10.10.0/24 (HR, Marketing, Management)

![[Assignment - 3 Department DHCP.png]]

---

| Department  | Subnet              | Subnet Mask        | Gateway        | Usable IP Range           | Broadcast        |
|-------------|---------------------|---------------------|----------------|---------------------------|------------------|
| HR          | 10.10.10.0/28       | 255.255.255.240     | 10.10.10.1     | 10.10.10.2 – 10.10.10.14   | 10.10.10.15      |
| Marketing   | 10.10.10.16/28      | 255.255.255.240     | 10.10.10.17    | 10.10.10.18 – 10.10.10.30  | 10.10.10.31      |
| Management  | 10.10.10.32/28      | 255.255.255.240     | 10.10.10.33    | 10.10.10.34 – 10.10.10.46  | 10.10.10.47      |

---
enable
configure terminal

! === Interface Configuration ===
! HR Interface (10.10.10.0/28 -> 255.255.255.240)
interface gigabitEthernet 0/0
ip address 10.10.10.1 255.255.255.240
no shutdown
exit

! Marketing Interface (10.10.10.16/28 -> 255.255.255.240)
interface gigabitEthernet 0/1
ip address 10.10.10.17 255.255.255.240
no shutdown
exit

! Management Interface (10.10.10.32/28 -> 255.255.255.240)
interface gigabitEthernet 0/2
ip address 10.10.10.33 255.255.255.240
no shutdown
exit

! === Exclude Gateway IPs from DHCP ===
ip dhcp excluded-address 10.10.10.1
ip dhcp excluded-address 10.10.10.17
ip dhcp excluded-address 10.10.10.33

! === DHCP Pool for HR Department ===
ip dhcp pool HR
network 10.10.10.0 255.255.255.240
default-router 10.10.10.1
dns-server 8.8.8.8
exit

! === DHCP Pool for Marketing Department ===
ip dhcp pool Marketing
network 10.10.10.16 255.255.255.240
default-router 10.10.10.17
dns-server 8.8.8.8
exit

! === DHCP Pool for Management Department ===
ip dhcp pool Management
network 10.10.10.32 255.255.255.240
default-router 10.10.10.33
dns-server 8.8.8.8
exit

---