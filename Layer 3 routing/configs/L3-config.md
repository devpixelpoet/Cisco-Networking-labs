
# 🎛️ Multilayer Switch Configuration Commands (Cisco CLI)

This file contains the core Layer 3 switching commands utilized on the **3560 Multilayer Switch** to enable hardware-accelerated routing and Switched Virtual Interfaces (SVIs).

```vlan
Switch> enable
Switch# configure terminal

! Enable global IP Routing functionality on the Multilayer Switch
Switch(config)# ip routing

! Configure a Switched Virtual Interface (SVI) for Vlan 1 (End-Device Gateway)
Switch(config)# interface vlan 1
Switch(config-if)# ip address 192.168.10.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

! Transform a standard Layer 2 port into a routed Layer 3 interface
Switch(config)# interface fastEthernet 0/1
Switch(config-if)# no switchport
Switch(config-if)# ip address 192.168.3.2 255.255.255.252
Switch(config-if)# no shutdown
Switch(config-if)# exit

! --- STATIC ROUTING CONFIGURATION ---
! Set up a gateway pattern or static paths to reach external router networks
Switch(config)# ip route 192.168.4.0 255.255.255.0 192.168.3.1
Switch(config)# ip route 192.168.5.0 255.255.255.0 192.168.3.1

Switch(config)# end
Switch# copy running-config startup-config
