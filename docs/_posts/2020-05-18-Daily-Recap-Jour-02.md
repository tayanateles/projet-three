---
layout: post
title:  "Daily Recap JOUR 02"
date:   2020-05-19
categories: welcome
---


## Réalisations de la journée :

- Adressage Ipv4 et Ipv6 
  - [x] Tableau adresssage IPv4
  - [ ] Tableau adresssage IPv6
  - [x] Validation IPv4
  - [ ] Validation Ipv6
 

 - Prise en main de Ansible

 - Tableau comparatif OSPF/EIGRP

| OSPF  | EIGRP          |
|---|-----|
| A état de liens | A vecteur de distance sans boucles 
| Seulement IP | multi-protocoles
| Il ne possède pas de route secondaire | Il possède une route secondaire
| Utilise des aires pour limiter l'utilisation de la bande passante| Système autonome
| Aucunes limite de sauts | Maximum 224 sauts 
| Distance administrative 90 | Distance administrative 110


  - [x] Mise en place de la topologie Switchblock
    - configuration globale
    - création VLANs
    - configuration ports access/trunk
    - configuration etherchannel
    - configuration RTSP
    - configuration HSRP
    - configuration DHCP

  

  - [x] Mise en place de la topologie Tripod
    - configuration Ipv4
    - configuration DHCP
    - configuration EIGRP
    - configuration NAT
 
  - Debrieffing
  
> Nous avons rencontré un problème lors de la copie du fichier "Ansible-ccna_lab/roles". 
> Il n'était pas cosidéré comme un lien mais  comme un fichier. 
> Nous avons finalement reussi à résoudre ce problème avec la commande `ln -s` directement sur le Pc de contrôle centos. 
> 
> Par la suite, nous avons rencontré de nombreuses erreurs de syntaxe sur nos fichiers `hosts`.
> Nous avons commencé à les résoudre.
> **la topologie n'est pas fonctionnelle pour le moment.**

 - Update docs
   - [x] Update Scrum
   - [x] Update Blog
   - [x] Update [Topologie.PNG](https://github.com/reseau-2020/projet-three/blob/master/Topologie.PNG)
    
    
## Programme du 20.05.2020
 
 - Terminer la mise en route de la topologie sur Ipv4 en corrigeant les erreurs de syntaxes
 - Diagnostiquer le bon fonctionnement de la topologie
 - Réaliser un tableau d'adressage IPv6
 - Commencer le lancement de la topologie en IPv6
 
 
  
