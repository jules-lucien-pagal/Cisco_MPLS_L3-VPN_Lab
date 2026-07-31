🔧 MPLS L3-VPN & LAN ROUTING Project --- Cisco

Niveau : Intermédiaire
Dans ce lab, je compte déployer une infrastructure BACKBONE MPLS [PEs] qui tourne sur Cisco avec raccordement des Clients [CEs].
L’objectif principal est de garantir le routage basé sur les Labels , le trafic venant du Lan est transporté sur le réseau Backbone et acheminé vers les Clients raccordés.
(LDP , LSP , Traffic Engineering , ..)

🧩 Contexte technique
~ OSPF utilisé comme IGP sur la partie Lan avec PBR
~ MP-BGP , iBGP unicast et VPNv4/v6 utilisés sur la partie Wan pour le peering vers les routeurs PEs du Backbone (Peering sur les Loopbacks)
~ OSPF & BGP Gracefull-restart/NSR
~ ISIS utilisé comme IGP au sein du Backbone entre PEs pour garantir la connectivité Inter-PEs
~ Redistribution bidirectionnelle entre OSPF ↔ BGP afin de garantir l'import et export des routes
~ eBGP utilisé sur la partie Wan pour le peering CEs↔PEs afin d'éviter les redistributions supplémentaires
~ VRFs , RT , RD pour instancier et labeliser le trafic venant des différents Clients CEs

🎯 Objectifs du lab
~ Routage Lan et Wan 
~ Assurer l'acheminement du trafic entre sites via le Backbone
~ Les Switchs Coeurs (SW_CORE_x) assurent le routage inter-vlan
~ Les Switchs D'accès (SW_ACC_x) assurent la connectivité end-user (PCs,Printers, ...)
~ Les PC_x sont les PCs utilisateurs Lan
~ PEs sont les Providers Edge | CEs sont les Customers Edge
~ PE_01_RR1 et PE_02_RR2 sont les Routes Reflectors qui reflètent les routes non connectées physiquement vers les autres PEs
