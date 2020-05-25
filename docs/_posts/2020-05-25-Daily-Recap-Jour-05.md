---
layout: post
title:  "Daily Recap JOUR 05"
date:   2020-05-25
categories: welcome
---


## Réalisations de la journée :

 - IPv6
   - [x] Déploiement IPv6
   - [x] Connectivité vers Internet
   - [ ] DNS
 
 - [x] NTP
 

## Débriefing

### Connectivité IPv6 vers Internet

Dans un premier temps, afin de déployer la connectivité vers l'internet, nous avions configuré une adresse statique en IPV6 `ipv6 route ::/0 g0/0 FE80::E53:21FF:FE38:5800` avec :
 - `FE80::E53:21FF:FE38:5800` , l'adresse link-local de notre passerelle vers l'internet
 - `g0/0` notre interface de sortie vers l'extérieur

Avec un `show ipv6 route`sur R2 et R3, nous nous sommes aperçu que la route ne se distribuait pas automatiquement. Nous avons donc déployer `ipv6 route ::/0 g0/1 FE80::1` sur ces derniers.

Cela n'était pas nécessaire. Nous aurions pu forcer R1 à distribuer cette route statique :
``
ipv6 router eigrp 1
redistribute static
`` 
Par ailleurs, il est plus correct de limiter la route par défaut aux adresses publiques : `ipv6 route 2000::/3 g0/0 FE80::E53:21FF:FE38:5800`.

Nous avons fait le choix de ne pas déployer de LAN directement connectée sur R1. Par conséquent, aucune interface de R1 ne dispose d'adresse publique et donc ne peut pas joindre directement internet. Il est nécessaire de `ping`à partir des PCs des VLANs.

Toutefois, aucune connectivité vers l'internet ou entre les différents PC est observée.

`show ipv6 route` sur DS1 et DS2 nous apprend qu'il n'y a pas de route apprise par eigrp vers l'internet.
`show ipv6 eigrp neighbors`sur DS1 nous apprend qu'il ne voit pas R2 correctement.
`show run | b ipv6 eigrp`sur R2 nous apprend que l'interface G0/4 n'est pas montée en eigrp.

Sur R2 :
``
int g0/4
ipv6 eigrp 1
`` 
On remarque un log de eigrp nous indiquant qu'une nouvelle route a été apprise. Les `ping ipv6` de PC1 vers PC8 et de PC1 vers l'internet fonctionnent correctement.

### NTP

Nous avons d'abord ajusté l'heure de tous les périphériques Cisco :

``
(config)#clock timezone GMT +1
(config)#clock summer-time FR recurring last SUN MAR 02:00 last SUN OCT 02:00
``

Deuxièmement, nous avons paramétré un server NTP publique sur R1 : 

``
(config)#ntp server 3.fr.pool.ntp.org
(config)#ntp update-calendar
``

Ensuite, nous avons configuré une interface R1 (10.1.1.1) en tant que serveur NTP pour les autres périphériques Cisco :

``
(config)#ntp server 10.1.1.1
(config)#ntp update-calendar
``

Nous avons constaté que les commutateurs AS1 et AS2 n'étaient pas synchronisés. Le problème a été résolu en désactivant le routage et en ajoutant une route par défaut sur ces deux périphériques, l'adresse utilisée a été la passerelle du sous-réseau virtuel de gestion (VLAN99).

``
(config)#no ip routing
(config)#ip default-gateway 10.192.1.252
``

### DNS 

`ping` et `ping ipv6 www.google.com` fonctionnent sur R1, R2, R3, DS1 et DS2. Mais pas sur les PCs. 

 
 

## Update docs

   - [x] Update Scrum
   - [x] Update Blog
   - [x] Update [Gantt_projet_3.xlsx](https://github.com/reseau-2020/projet-three/blob/master/Gantt_projet_3.xlsx)
    
    
## Programme du 26.05.2020
  
 - Mettre en place un pare-feu (Ipv4/Ipv6)
 - Mettre en place un VPN (Ipv4/Ipv6)
 
  
