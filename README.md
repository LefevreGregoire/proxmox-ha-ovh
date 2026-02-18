# Cluster Proxmox Haute Disponibilité & Ceph via OVHcloud

<p align="center">
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT"></a>
  <a href="https://www.proxmox.com/"><img src="https://img.shields.io/badge/Proxmox_VE-8.x-E57000?logo=proxmox&logoColor=white" alt="Proxmox VE"></a>
  <a href="https://ceph.com/"><img src="https://img.shields.io/badge/Ceph-Storage-EF3E36?logo=ceph&logoColor=white" alt="Ceph"></a>
  <a href="https://www.debian.org/"><img src="https://img.shields.io/badge/Debian-12_Bookworm-A81D33?logo=debian&logoColor=white" alt="Debian"></a>
  <a href="https://www.ovhcloud.com/"><img src="https://img.shields.io/badge/OVHcloud-Bare_Metal-012169?logo=ovh&logoColor=white" alt="OVHcloud"></a>
</p>

Ce projet a pour objectif de déployer un cluster Proxmox VE hautement disponible (HA) sur des serveurs dédiés OVHcloud, en utilisant Ceph pour le stockage distribué répliqué, avec une architecture hybride NVMe/HDD.

## Points Clés du Projet

* **Haute Disponibilité (HA) :** Basculement automatique (Failover) des machines virtuelles en moins de 2 minutes en cas de perte totale d'un serveur physique (Fencing via Watchdog).
* **Stockage Ceph Hybride (Tiering) :** Optimisation des performances sur des disques mécaniques capacitifs. L'OSD Ceph stocke les données sur un RAID 5 HDD (via `mdadm` + LVM), mais délègue sa base de données interne (DB/WAL BlueStore) sur un disque **NVMe dédié** pour absorber les I/O aléatoires.
* **Sécurité & Isolation :** Utilisation de l'Edge Network Firewall d'OVH en périphérie (Default DROP). Les flux critiques de synchronisation (Corosync) et de stockage (Ceph) sont totalement isolés sur un réseau privé **vRack** (10 Gbps / MTU 9000).

## Stack Technique

* **Hyperviseur :** Proxmox VE 8 (Debian)
* **Stockage Distribué :** Ceph (BlueStore)
* **Réseau :** OVH vRack (Réseau privé L2)
* **Système / Disques :** LVM, mdadm (RAID 5 Logiciel)

## Documentation Détaillée

Toute la démarche technique, l'architecture détaillée, la configuration réseau et les commandes de déploiement sont documentées dans le fichier principal :

**[Documentation complète (Documentation.md)](./Documentation.md)**

---
*Projet réalisé dans le cadre d'un déploiement d'infrastructure de production.*
