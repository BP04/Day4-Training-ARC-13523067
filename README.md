# Day 4 Training ARC

This is a repository created to fulfill ARC's day 4 assignment

## Configuration

### Router

```bash
enable
configure terminal
hostname College
enable secret class
service password-encryption
banner motd # something #

interface g0/0
 description Connection to LAN 10
 ip address 10.10.10.1 255.255.255.0
 ipv6 address 2001:DB8:ACAD:100::1/64
 no shutdown
 exit

interface g0/1
 description Connection to LAN 11
 ip address 10.10.11.1 255.255.255.0
 ipv6 address 2001:DB8:ACAD:200::1/64
 no shutdown
 exit

line console 0
 password cisco
 login
 exit

line vty 0 4
 password cisco
 login
 exit

copy running-config startup-config
```

### Switch 2

```bash
enable
configure terminal
hostname Class-B
enable secret class
service password-encryption
banner motd # something #

interface vlan 1
 description Management Interface
 ip address 10.10.11.100 255.255.255.0
 no shutdown
 exit

ip default-gateway 10.10.11.1

line console 0
 password cisco
 login
 exit

line vty 0 4
 password cisco
 login
 exit

copy running-config startup-config
```

### PC 1

IPv4: 10.10.10.101/24, Gateway: 10.10.10.1
IPv6: 2001:DB8:ACAD:100::50/64, Gateway: FE80::2

### PC 2

IPv4: 10.10.10.102/24, Gateway: 10.10.10.1
IPv6: 2001:DB8:ACAD:100::60/64, Gateway: FE80::2

### PC 3

IPv4: 10.10.11.101/24, Gateway: 10.10.11.1
IPv6: 2001:DB8:ACAD:200::50/64, Gateway: FE80::3

### PC 4

IPv4: 10.10.11.102/24, Gateway: 10.10.11.1
IPv6: 2001:DB8:ACAD:200::60/64, Gateway: FE80::3
