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
   - [ ] Ipv4
   - [ ] Ipv6
 - Organiser les services de surveillances
   - [x] Syslog
   - [ ] SNMP


## Débriefing

 > Sur R1, concurence sur le port UDP 123 avec NTP.
 > Le DNS se fonctionnne pas sur les PC. 
 > Debogage du VPN. 
 > Configuration des éléments en IPv4 en premier. 
 
### Le pare-feu

En premier, nous avons ajouter a notre topologie un dispositif de sécurité de type **Fortios** entre un PC-distant et l'Internet. 

Un pare-feu a été configurer en IPv4 sur ce Fortios avec sa console graphique. Ainsi que sur le routeur R1 sur la console de GNS3.

### Le VPN 

Le tunnel VPN IPSEC en IPv4 permettant une connexion depuis le PC-distant est en cours de configuration, il n'est pas fonctionnel. 


## Update docs

   - [x] Update Scrum
   - [x] Update Blog
   - [x] Update [Gantt_projet_3.xlsx](https://github.com/reseau-2020/projet-three/blob/master/Gantt_projet_3.xlsx)
    
    
## Programme du 27.05.2020
  
 - Mettre en place un pare-feu (Ipv6)
 - Mettre en place un VPN (Ipv4/Ipv6)
 - Mettre en place SNMP
  
