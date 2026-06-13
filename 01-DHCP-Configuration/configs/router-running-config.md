## 💻 Konfiguratsiya buyruqlari (Cisco CLI)

```cisco
Router> enable
Router# configure terminal

! DHCP Pool yaratish
Router(config)# ip dhcp pool LAN-1
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.1.1
Router(dhcp-config)# dns-server 1.1.1.1
Router(dhcp-config)# exit

! Gateway IP-ni tarqatishdan chiqarib tashlash
Router(config)# ip dhcp excluded-address 192.168.1.1

! Interfeysni sozlash va yoqish
Router(config)# interface fastEthernet 0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
