# 💻 Router 1 Configuration Commands (Cisco CLI)

This file contains the foundational Cisco IOS configuration commands deployed on **Router 1 (R1)** to establish Layer 3 routing and interface reachability.

```vlan
Router> enable
Router# configure terminal

! Change hostname for identification
Router(config)# hostname R1

! Configure the point-to-point WAN interface connecting to Router 2
R1(config)# interface fastEthernet 0/1
R1(config-if)# ip address 192.168.2.1 255.255.255.252
R1(config-if)# no shutdown
R1(config-if)# exit

! Configure the interface connecting to Multilayer Switch 0 / LAN
R1(config)# interface fastEthernet 0/0
R1(config-if)# ip address 192.168.4.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# exit

! --- STATIC ROUTING CONFIGURATION ---
! Routing traffic destined for the remote LAN (192.168.5.0/24) via Router 2 next-hop
R1(config)# ip route 192.168.5.0 255.255.255.0 192.168.2.2

! Routing traffic destined for the remote LAN (192.168.1.0/24) via Router 2 next-hop
R1(config)# ip route 192.168.1.0 255.255.255.0 192.168.2.2

R1(config)# end
R1# copy running-config startup-config
