---
layout: post
title:  "Daily Recap JOUR 06"
date:   2020-05-26
categories: welcome
---


## Réalisations de la journée :

 - Mettre en place un pare-feu 
   - [x] Ipv4
   - [ ] Ipv6
 - Mettre en place un VPN
   - [X] Ipv4
   - [ ] Ipv6
 - Organiser les services de surveillances
   - [x] Syslog
   - [ ] SNMP
 - [x] Debug DNS

## Débriefing

### Problèmes rencontrés

 > Sur R1, le pare-feu empêchait NTP de fonctionner correctement sur le port UDP 123.
 > Le DNS ne fonctionnnait pas sur les PCs. 
 > Debogage du VPN. Pas de connexion distante. 

### Les pare-feu
En premier, nous avons ajouter a notre topologie un dispositif de sécurité de type **Fortios** entre un PC-distant et l'Internet. 
Un pare-feu a été configurer en IPv4 sur ce Fortios avec sa console graphique. Ainsi que sur le routeur R1 sur la console de GNS3.

#### NTP et pare-feu Cisco R1
```
Dropping udp session 188.165.250.19:123 192.168.122.221:123 on zone-pair internet-self class class-default due to  DROP action found in policy-map with ip ident 23648
```
Une mise à jour des ACLs a été nécessaire.

#### PC pirate
L'ajout d'un pc pirate nous a permis de verifier les ports de R1.
```
Starting Nmap 6.40 ( http://nmap.org ) at 2020-05-26 11:51 CEST
Nmap scan report for 192.168.122.221
Host is up (0.97s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
MAC Address: 0C:D0:27:38:D0:00 (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 90.78 seconds
```
On remarquera que seul SSL est disponible.

#### Pare-feu Fortios
Une première configuration en console sur fortios a été réalisée :
```
configuration system interface
edit port1		
 set mode static			
 set ip 192.168.100.1 255.255.255.0
 append allowaccess http
edit port2
 append allowaccess http
edit port3
 append allowaccess http
config system dns
 set primary 1.1.1.1
 set secondary 8.8.8.8
end
```
On obtient les différentes IP des interfaces avec `get system interface physical`

#### Policy d'interdiction de facebook
Sur Fortios, pour s'amuser, nous avons ajouter une policy `lan > internet` avec un `deny` sur facebook.
Un `curl www.facebook.com` avant et après à partir du PC-distant nous a asssuré de son efficacité.

### Le VPN 

Le tunnel VPN IPSEC en IPv4 permettant une connexion depuis le PC-distant est en cours de configuration, **il n'est pas fonctionnel pour uen raison inconnue pour le moment**.

Grâce à l'aide de François B. et G., nous avons effectué les changements nécessaire sur l'encryption et authentification (en phase 1 et phase 2) sur les 2 pare-feu.
```
Phase 1 : 3DES Encryption and SHA Authentication
Phase 2 : 3DES Encryption and SHA Authentication
Set the Diffie-Hellman Group to 5
``` 
### DNS

Nous avions un problème de DNS sur les PCs des VLANs. Nous avons remarqué que les dns-server des VLANs n'étaient pas paramétrés.
Sur DS1 et DS2 :
```
ip dhcp pool VLAN10
 dns-server 1.1.1.1
ip dhcp pool VLAN20
 dns-server 1.1.1.1
ip dhcp pool VLAN30
 dns-server 1.1.1.1
ip dhcp pool VLAN40
 dns-server 1.1.1.1
 ```
 Un `ping` en IPv4 et IPv6 des PCs vers `www.google.com` nous a rassuré sur son fonctionnement.

## Update docs

   - [x] Update Scrum
   - [x] Update Blog
   - [x] update [Topologie](https://github.com/reseau-2020/projet-three/blob/master/topologie20200526.png?raw=true)
   - [x] Update [Gantt_projet_3.xlsx](https://github.com/reseau-2020/projet-three/blob/master/Gantt_projet_3.xlsx)
    
    
## Programme du 27.05.2020
  
 - Mettre en place un pare-feu (Ipv6)
 - Mettre en place un VPN (Ipv4/Ipv6)
 - Mettre en place SNMP
  
