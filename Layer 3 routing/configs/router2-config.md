# 💻 Router 2 Configuration Commands (Cisco CLI)

This file contains the operational Cisco IOS configuration commands deployed on **Router 2 (R2)** to handle next-hop routing and LAN/WAN interface management.

```vlan
Router> enable
Router# configure terminal

! Change hostname for identification
Router(config)# hostname R2

! Configure the point-to-point WAN interface connecting back to Router 1
R2(config)# interface fastEthernet 0/1
R2(config-if)# ip address 192.168.2.2 255.255.255.252
R2(config-if)# no shutdown
R2(config-if)# exit

! Configure the interface connecting to the local LAN segment / Switch 1
R2(config)# interface fastEthernet 0/0
R2(config-if)# ip address 192.168.5.1 255.255.255.0
R2(config-if)# no shutdown
R2(config-if)# exit

! --- STATIC ROUTING CONFIGURATION ---
! Routing traffic destined for the remote Router 1 LAN (192.168.4.0/24) via R1 next-hop
R2(config)# ip route 192.168.4.0 255.255.255.0 192.168.2.1

! Routing traffic destined for the primary core network (192.168.1.0/24) via R1 next-hop
R2(config)# ip route 192.168.1.0 255.255.255.0 192.168.2.1

R2(config)# end
R2# copy running-config startup-config
