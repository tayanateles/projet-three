# PLAN D'ADRESSAGE
Passerelle vers l'internet Ipv6 : fe80::e53:21ff:fe38:5800

| Périphérique  |Interfaces  |Infos  | Adresse ipv4  | IPv6 Link-local | IPv6 privée | IPv6 publique |
|:---:|:-----:|:-----:|:----:|:----:|:----:|:----:|
R1 | Gi0/0 | connected to INTERNET | dhcp | fe80::1 | fe80::cafe:3 | 2001:470:c814:3000::1 |
R1 | Gi0/2 | connected to R2 on port Gi0/1 | 10.1.1.1 | fe80::1 | fd00:470:c814:3000::1 | 2001:470:c814:3000::1 |
R1 | Gi0/3 | connected to R3 on port Gi0/1 | 10.1.2.1 | fe80::1 | fd00:470:c814:3000::1 | 2001:470:c814:3000:1::1 |  
R2 | Gi0/1 | connected to R1 on port Gi0/2 | 10.1.1.2 | fe80::2 | fd00:470:c814:3000::2 | 2001:470:c814:3000:2::2 | 
R2 | Gi0/2 | connected to DS1 on port Gi2/0 | 10.2.1.2 | fe80::2 | fd00:470:c814:3000::2 | 2001:470:c814:3000:2::2 | 
R2 | Gi0/3 | connected to R3 on port Gi0/2 | 10.1.3.2| fe80::2 | fd00:470:c814:3000::2 | 2001:470:c814:3000:2::2 | 
R2 | Gi0/4 | connected to DS1 on port Gi3/0 | 10.2.2.2 | fe80::2 | fd00:470:c814:3000::2 | 2001:470:c814:3000:2::2 | 
R2 | Gi0/5 | connected to DS2 on port Gi2/1 | 10.2.3.2 | fe80::2 | fd00:470:c814:3000::2 | 2001:470:c814:3000:2::2 | 
R2 | Gi0/6 | connected to DS2 on port Gi3/1 | 10.2.4.2 | fe80::2 | fd00:470:c814:3000::2 | 2001:470:c814:3000:2::2 | 
R3 | Gi0/1 | connected to R1 on port Gi0/3 | 10.1.2.3 | fe80::3 | fd00:470:c814:3000::3 | 2001:470:c814:3000:3::3 | 
R3 | Gi0/2 | connected to R2 on port Gi0/3 | 10.1.3.3 | fe80::3 | fd00:470:c814:3000::3 | 2001:470:c814:3000:3::3 | 
R3 | Gi0/3 | connected to DS2 on port Gi2/0 | 10.3.1.3 | fe80::3 | fd00:470:c814:3000::3 | 2001:470:c814:3000:3::3 | 
R3 | Gi0/4 | connected to DS2 on port Gi3/0 | 10.3.2.3 | fe80::3 | fd00:470:c814:3000::3 | 2001:470:c814:3000:3::3 | 
R3 | Gi0/5 | connected to DS1 on port Gi2/1 | 10.3.3.3 | fe80::3 | fd00:470:c814:3000::3 | 2001:470:c814:3000:3::3 | 
R3 | Gi0/6 | connected to DS1 on port Gi3/1 | 10.3.4.3 | fe80::3 | fd00:470:c814:3000::3 | 2001:470:c814:3000:3::3 | 
DS1 | Gi2/0 | connected to R2 on port Gi0/2 | 10.2.1.1 | fe80::d1 | fd00:470:c814:3000::d1 | 2001:470:c814:3000:d::d1 | 
DS1 | Gi3/0 | connected to R2 on port Gi0/4 | 10.2.2.1 | fe80::d1 | fd00:470:c814:3000::d1 | 2001:470:c814:3000:d::d1 | 
DS1 | Gi2/1 | connected to R3 on port Gi0/5 | 10.3.3.1 | fe80::d1 | fd00:470:c814:3000::d1 | 2001:470:c814:3000:d::d1 | 
DS1 | Gi3/1 | connected to R3 on port Gi0/6 | 10.3.4.1 | fe80::d1 | fd00:470:c814:3000::d1 | 2001:470:c814:3000:d::d1 | 
DS2 | Gi2/1 | connected to R2 on port Gi0/5 | 10.2.3.1 | fe80::d2 | fd00:470:c814:3000::d2 | 2001:470:c814:3000:d::d2 | 
DS2 | Gi3/1 | connected to R2 on port Gi0/6 | 10.2.4.1 | fe80::d2 | fd00:470:c814:3000::d2 | 2001:470:c814:3000:d::d2 | 
DS2 | Gi2/0 | connected to R3 on port Gi0/3 | 10.3.1.2 | fe80::d2 | fd00:470:c814:3000::d2 | 2001:470:c814:3000:d::d2 | 
DS2 | Gi3/0 | connected to R3 on port Gi0/4 | 10.3.2.2 | fe80::d2 | fd00:470:c814:3000::d2 | 2001:470:c814:3000:d::d2 | 

Passerelle IPv6 vers l'internet : fe80::e53:21ff:fe38:5800

# VLANS
VLAN | IPv4 | Passerelle | Port Access (AS1 et AS2) | IPv6 Virtuelle |
|:---:|:-----:|:----:|:----:|:----:|
| vlan 10 | 10.192.10.0/24 | 10.192.10.254 | Gi2/0 | fe80::a10
| vlan 20 | 10.192.20.0/24 | 10.192.20.254 | Gi2/1 | fe80::a20
| vlan 30 | 10.192.30.0/24 | 10.192.30.254 | Gi2/2 | fe80::a30
| vlan 40 | 10.192.40.0/24 | 10.192.40.254 | Gi2/3 | fe80::a40
| vlan 99 | vlan natif | 10.192.1.254 | - | fe80::d99:99

## Portchannel
| Périphérique  | PortChannel | Port Physique |  Infos
|:---:|:-----:|:----:|:----:|
DS1 | po1 | Gi0/0, Gi1/0 | Link to AS1 |
DS1 | po11 | Gi0/1, Gi1/1 | Link to AS2 |
DS1 | po3 | Gi0/2, Gi1/2 | Link to DS2 | 
DS2 | po2 | Gi0/0, Gi1/0 | Link to AS2 |
DS2 | po22 | Gi0/1, Gi1/1 | Link to AS1 |
DS2 | po3 | Gi0/2, Gi1/2  | Link to DS1 |

## Spanning-Tree
| Périphérique  | Interface | Spanning-Tree |  Adresse ipv4 | IPv6 Link-local | IPv6 privée | IPv6 publique |
|:---:|:-----:|----|:----:|:----:|:----:|:----:|
DS1 | VLAN10 | Root Primary | 10.192.10.252/24 | fe80::d1:10 | fd00:470:c814:3000:10::252 | 2001:470:c814:3000:10::252 | 
DS1 | VLAN20 | Root Secondary | 10.192.20.252/24 | fe80::d1:20 | fd00:470:c814:3000:20::252 | 2001:470:c814:3000:20::252 |
DS1 | VLAN30 | Root Primary | 10.192.30.252/24 | fe80::d1:30 | fd00:470:c814:3000:30::252 | 2001:470:c814:3000:30::252 |
DS1 | VLAN40 | Root Secondary | 10.192.40.252/24 | fe80::d1:40 | fd00:470:c814:3000:40::252 | 2001:470:c814:3000:40::252 |
DS2 | VLAN10 | Root Secondary | 10.192.10.253/24 | fe80::d2:10 | fd00:470:c814:3000:10::253 | 2001:470:c814:3000:10::253 |
DS2 | VLAN20 | Root Primary | 10.192.20.253/24 | fe80::d2:20 | fd00:470:c814:3000:20::253 | 2001:470:c814:3000:20::253 |
DS2 | VLAN30 | Root Secondary | 10.192.30.253/24 | fe80::d2:30 | fd00:470:c814:3000:30::253 | 2001:470:c814:3000:30::253 |
DS2 | VLAN40 | Root Primary | 10.192.40.253/24 | fe80::d2:40 | fd00:470:c814:3000:40::253 | 2001:470:c814:3000:40::253 |
