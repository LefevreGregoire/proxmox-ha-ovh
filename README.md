# 🚀 Proxmox VE High-Availability Cluster & Ceph on OVHcloud

Bienvenue sur le dépôt de mon projet d'infrastructure hyper-convergée (HCI). 

Ce projet a pour objectif de déployer un cluster Proxmox VE hautement disponible (HA) sur des serveurs dédiés OVHcloud, en utilisant Ceph pour le stockage distribué répliqué, avec une architecture hybride NVMe/HDD.

## 🌟 Points Clés du Projet

* **Haute Disponibilité (HA) :** Basculement automatique (Failover) des machines virtuelles en moins de 2 minutes en cas de perte totale d'un serveur physique (Fencing via Watchdog).
* **Stockage Ceph Hybride (Tiering) :** Optimisation des performances sur des disques mécaniques capacitifs. L'OSD Ceph stocke les données sur un RAID 5 HDD (via `mdadm` + LVM), mais délègue sa base de données interne (DB/WAL BlueStore) sur un disque **NVMe dédié** pour absorber les I/O aléatoires.
* **Sécurité & Isolation :** Utilisation de l'Edge Network Firewall d'OVH en périphérie (Default DROP). Les flux critiques de synchronisation (Corosync) et de stockage (Ceph) sont totalement isolés sur un réseau privé **vRack** (10 Gbps / MTU 9000).

## 🛠️ Stack Technique

* **Hyperviseur :** Proxmox VE 8 (Debian)
* **Stockage Distribué :** Ceph (BlueStore)
* **Réseau :** OVH vRack (Réseau privé L2)
* **Système / Disques :** LVM, mdadm (RAID 5 Logiciel)

## 📖 Documentation Détaillée

Toute la démarche technique, l'architecture détaillée, la configuration réseau et les commandes de déploiement sont documentées dans le fichier principal :

👉 **[Consulter la documentation complète (DOCUMENTATION.md)](./DOCUMENTATION.md)**

---
*Projet réalisé dans le cadre d'un déploiement d'infrastructure de production.*
