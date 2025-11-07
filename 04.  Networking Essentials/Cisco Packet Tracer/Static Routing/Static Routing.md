![[04.  Networking Essentials/Cisco Packet Tracer/Static Routing/staticrouting.png]]

---

! ===== Router R1 (Kathmandu) =====
enable
configure terminal

! Interface for LAN1 (50.0.0.0/24)
interface gigabitEthernet 0/1
ip address 50.0.0.1 255.255.255.0
no shutdown
exit

! Interface for LAN2 (60.0.0.0/24)
interface gigabitEthernet 0/2
ip address 60.0.0.1 255.255.255.0
no shutdown
exit

! Interface for R1-R2 link (100.0.0.0/30)
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

! Static routes to Pokhara networks via R2
ip route 70.0.0.0 255.255.255.0 100.0.0.2
ip route 80.0.0.0 255.255.255.0 100.0.0.2

end

! ===== Router R2 (Pokhara) =====
enable
configure terminal

! Interface for R1-R2 link (100.0.0.0/30)
interface gigabitEthernet 0/0
ip address 100.0.0.2 255.255.255.252
no shutdown
exit

! Interface for LAN3 (70.0.0.0/24)
interface gigabitEthernet 0/1
ip address 70.0.0.1 255.255.255.0
no shutdown
exit

! Interface for LAN4 (80.0.0.0/24)
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

! Static routes to Kathmandu networks via R1
ip route 50.0.0.0 255.255.255.0 100.0.0.1
ip route 60.0.0.0 255.255.255.0 100.0.0.1

end
