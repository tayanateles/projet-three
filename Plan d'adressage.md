# PLAN D'ADRESSAGE (a modifier)
| Périphérique  |Interfaces  |Infos  | Adresse ipv4  |  Adresse ipv6
|---|-----|-----|----|----|
R1 | Gi0/0 | connected to SW-internet on port Ethernet0 |  | 
R1 | Gi0/2 | connected to R2 on port Gi0/1 | 10.1.1.1 | 
R1 | Gi0/3 | connected to R3 on port Gi0/1 | 10.1.2.1 | 
R1 | Gi0/7 | connected to SW-CTRL on port Ethernet1 |  | 
R2 | Gi0/1 | connected to R1 on port Gi0/2 | 10.1.1.2 | 
R2 | Gi0/2 | connected to DS1 on port Gi2/0 | 10.2.1.2 | 
R2 | Gi0/3 | connected to R3 on port Gi0/2 | 10.1.3.2| 
R2 | Gi0/4 | connected to DS1 on port Gi3/0 | 10.2.2.2 | 
R2 | Gi0/5 | connected to DS2 on port Gi2/1 | 10.2.3.2 | 
R2 | Gi0/6 | connected to DS2 on port Gi3/1 | 10.2.4.2 | 
R2 | Gi0/7 | connected to SW-CTRL on port Ethernet2 |  | 
R3 | Gi0/1 | connected to R1 on port Gi0/3 | 10.1.2.3 | 
R3 | Gi0/2 | connected to R2 on port Gi0/3 | 10.1.3.3 | 
R3 | Gi0/3 | connected to DS2 on port Gi2/0 | 10.3.1.3 | 
R3 | Gi0/4 | connected to DS2 on port Gi3/0 | 10.3.2.3 | 
R3 | Gi0/5 | connected to DS1 on port Gi2/1 | 10.3.3.3 | 
R3 | Gi0/6 | connected to DS1 on port Gi3/1 | 10.3.4.3 | 
R3 | Gi0/7 | connected to SW-CTRL on port Ethernet3 |  | 
DS1 | Gi0/0 | connected to AS1 on port Gi0/0 |  | 
DS1 | Gi0/1 | connected to AS2 on port Gi0/1 |  | 
DS1 | Gi0/2 | connected to DS2 on port Gi0/2 |  | 
DS1 | Gi1/0 | connected to AS1 on port Gi1/0 |  | 
DS1 | Gi1/1 | connected to AS2 on port Gi1/1 |  | 
DS1 | Gi1/2 | connected to DS2 on port Gi1/2 |  | 
DS1 | Gi2/0 | connected to R2 on port Gi0/2 |  | 
DS1 | Gi2/1 | connected to R3 on port Gi0/5 |  | 
DS1 | Gi3/0 | connected to R2 on port Gi0/4 |  | 
DS1 | Gi3/1 | connected to R3 on port Gi0/6 |  | 
DS1 | Gi3/3 | connected to SW-CTRL on port Ethernet4 |  | 
DS2 | Gi0/0 | connected to AS2 on port Gi0/0 |  | 
DS2 | Gi0/1 | connected to AS1 on port Gi0/1 |  | 
DS2 | Gi0/2 | connected to DS1 on port Gi0/2 |  | 
DS2 | Gi1/0 | connected to AS2 on port Gi1/0 |  | 
DS2 | Gi1/1 | connected to AS1 on port Gi1/1 |  | 
DS2 | Gi1/2 | connected to DS1 on port Gi1/2 |  | 
DS2 | Gi2/0 | connected to R3 on port Gi0/3 |  | 
DS2 | Gi2/1 | connected to R2 on port Gi0/5 |  | 
DS2 | Gi3/0 | connected to R3 on port Gi0/4 |  | 
DS2 | Gi3/1 | connected to R2 on port Gi0/6 |  | 
DS2 | Gi3/3 | connected to SW-CTRL on port Ethernet5 |  |  
AS1  |  Gi0/0  |  connected to DS1 on port Gi0/0   |  | 
AS1  |  Gi0/1  |  connected to DS2 on port Gi0/1   |  | 
AS1  |  Gi1/0  |  connected to DS1 on port Gi1/0   |  | 
AS1  |  Gi1/1  |  connected to DS2 on port Gi1/1   |  | 
AS1  |  Gi2/0  |  connected to pc-1 on port eth0   |  | 
AS1  |  Gi2/1  |  connected to pc-2 on port eth0   |  | 
AS1  |  Gi2/2  |  connected to pc-3 on port eth0   |  | 
AS1  |  Gi2/3  |  connected to pc-4 on port eth0   |  | 
AS1  |  Gi3/3  |  connected to SW-CTRL on port Ethernet6 |  | 
AS2 | Gi0/0 | connected to DS2 on port Gi0/0 |  | 
AS2 | Gi0/1 | connected to DS1 on port Gi0/1 |  | 
AS2 | Gi1/0 | connected to DS2 on port Gi1/0 |  | 
AS2 | Gi1/1 | connected to DS1 on port Gi1/1 |  | 
AS2 | Gi2/0 | connected to pc-5 on port eth0 |  | 
AS2 | Gi2/1 | connected to pc-6 on port eth0 |  | 
AS2 | Gi2/2 | connected to pc-7 on port eth0 |  | 
AS2 | Gi2/3 | connected to pc-8 on port eth0 |  | 
AS2 | Gi3/3 | connected to SW-CTRL on port Ethernet7 |  | 


# VLANS
- vlan 10 : 10.192.10.0/24, ip default gateway 10.192.10.254
- vlan 20 : 10.192.20.0/24, passerelle 10.192.20.254
- vlan 30 : 10.192.30.0/24, passerelle 10.192.30.254
- vlan 40 : 10.192.40.0/24, passerelle 10.192.40.254
- vlan 99 : vlan natif

| Périphérique  |VLAN | Adresse ipv4  |  Adresse ipv6
|---|-----|----|----|
DS1 | VLAN10 | 10.192.10.252/24 | fd00:abc:10::1/24 ; 2001:470:c814:4010::1/64
DS1 | VLAN20 | 10.192.20.252/24 | fd00:abc:20::1/24 ; 2001:470:c814:4020::1/64 
DS1 | VLAN30 | 10.192.30.252/24 | fd00:abc:30::1/24 ; 2001:470:c814:4030::1/64
DS1 | VLAN40 | 10.192.40.252/24 | fd00:abc:40::1/24 ; 2001:470:c814:4040::1/64
DS2 | VLAN10 | 10.192.10.253/24 | fd00:abc:10::2/24 ; 2001:470:c814:4010::2/64
DS2 | VLAN20 | 10.192.20.253/24 | fd00:abc:20::2/24 ; 2001:470:c814:4020::2/64
DS2 | VLAN30 | 10.192.30.253/24 | fd00:abc:30::2/24 ; 2001:470:c814:4030::2/64
DS2 | VLAN40 | 10.192.40.253/24 | fd00:abc:40::2/24 ; 2001:470:c814:4040::2/64
