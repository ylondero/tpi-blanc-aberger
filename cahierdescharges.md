# Procédure de qualification : Informaticien/ne CFC
## Cahier des charges - TPI à blanc

---

## 1. INFORMATIONS GÉNÉRALES

**Candidat**  
- Nom : BERGER  
- Prénom : Antoine  
- Email : antoine.berger@epfl.ch  
- Lieu de travail : EPFL - ENAC-IT  
  Rte Cantonale, 1015 Lausanne

**Orientation**  
☒ Exploitation et infrastructure

**Chef de projet**  
- Nom : LONDERO  
- Prénom : Maeva  
- Email : maeva.londero@epfl.ch  
- Tél : 079 935 03 25

**Période de réalisation**  
3 jours (dates à définir)

**Horaire de travail**  
Lundi, mardi, mercredi : 8h-12h / 13h-17h35  
Pauses : 20 minutes le matin / 15 minutes l'après-midi

**Nombre d'heures**  
24 heures (3 x 8h)

**Planning**
- Analyse : 10% → 2.5h
- Implémentation : 60% → 14.5h
- Tests : 5% → 1h
- Documentation : 25% → 6h

---

## 2. PROCÉDURE

- Le candidat réalise un travail personnel sur la base de ce cahier des charges.
- Le cahier des charges est présenté, commenté et discuté avec le candidat. Par sa signature, le candidat accepte le travail proposé.
- Le candidat a connaissance de la grille d'évaluation avant de débuter le travail.
- Le candidat est entièrement responsable de la sécurité de ses données.
- En cas de problèmes graves, le candidat avertit au plus vite son chef de projet.
- Le candidat a la possibilité d'obtenir de l'aide, mais doit le mentionner dans son dossier.
- À la fin du délai imparti, le candidat doit transmettre le dossier de projet au chef de projet (version électronique + copie papier).

---

## 3. TITRE

**Infrastructure virtualisée Proxmox avec services Docker interconnectés**

---

## 4. MATÉRIEL ET LOGICIEL À DISPOSITION

- VM puissante (xaas) pour installer Proxmox VE
- Accès réseau et internet
- Documentation personnelle et accès à la documentation officielle Proxmox
- Accès aux repos Docker Hub

---

## 5. PRÉREQUIS

- Connaissances en virtualisation (VM, containers)
- Bonnes bases Linux (CLI, networking, services système)
- Connaissances Docker et docker-compose
- Compréhension des réseaux (VLAN, routage, NAT)

---

## 6. DESCRIPTIF DU PROJET

Antoine sera chargé de mettre en place une infrastructure virtualisée complète basée sur Proxmox VE. Le projet consiste à créer 2 machines virtuelles hébergeant des services Docker qui devront communiquer entre eux pour former une stack applicative fonctionnelle.

### Objectifs principaux

1. **Installation et configuration Proxmox VE**
   - Installation de l'hyperviseur Proxmox
   - Configuration réseau de base
   - Configuration du stockage

2. **Déploiement de VMs/Containers**
   - Création de 2 VMs 
   - Installation de Docker sur chaque instance
   - Configuration réseau pour permettre la communication inter-VMs

3. **Stack applicative avec Docker**
   - Déploiement d'une application multi-services (exemple : nginx reverse proxy + application web + base de données)
   - Les services Docker doivent être sur des VMs différentes
   - Configuration de la communication entre les services

4. **Documentation**
   - Documentation technique complète
   - Procédures de déploiement
   - Architecture et schémas réseau

Stack suggérée

**Service de gestion de tâches**
- VM1 : Nginx reverse proxy
- VM2 : Application Kanboard (outil de gestion de projets open-source, déjà packagé)
- VM3 : SQLite ou PostgreSQL
- **Besoin** : Interface web fonctionnelle pour créer/voir des tâches

---

## 7. ÉTAPES DU PROJET

Avant de commencer, tu dois créer un diagramme de Gantt ou un planning détaillé.

### Jour 1 - Installation et configuration de base

**Étape 1 : Planification de l'infrastructure**

- Définir l'architecture réseau

**Objectif 2 : Communication inter-VMs sécurisée**
- Les VMs peuvent se pinguer entre elles
- Configuration réseau documentée (adresses IP, routes, firewall)
- La base de données n'est accessible QUE depuis la VM application (pas depuis l'extérieur)

**Objectif 3 : Stack applicative fonctionnelle**
- Tous les services Docker déployés via docker-compose
- Le reverse proxy route correctement vers l'application
- L'application communique avec la base de données
- 
**Objectif 4 : Persistance et résilience**
- Les données persistent après redémarrage des containers
- Au moins un snapshot Proxmox créé et testé
- Procédure de restauration documentée

**Objectif 5 : Documentation professionnelle**
- Architecture réseau avec schéma clair (draw.io, excalidraw, etc.)
- README structuré avec procédure d'installation
- Tous les fichiers de configuration commentés
- Journal de travail quotidien avec problèmes rencontrés et solutions

### Gestion du temps recommandée

- **Analyse et planification** : ~10% (2.5h)
- **Implémentation** : ~60% (14.5h)
- **Tests et validation** : ~5% (1h)
- **Documentation** : ~25% (6h)

⚠️ **Important** : Ces pourcentages sont indicatifs. C'est à toi de gérer ton temps pour atteindre tous les objectifs dans les 24h imparties.

---

## 8. LIVRABLES

Le candidat est responsable de livrer à son chef de projet :

- **Jour 1 (fin de journée)** : Planification détaillée + architecture réseau (schéma)
- **Jour 2 (fin de journée)** : Rapport d'avancement + premiers tests fonctionnels
- **Jour 3 (fin de journée)** :
  - Documentation complète (format Markdown dans un repo Git)
  - Tous les fichiers de configuration (docker-compose.yml, configs Nginx, etc.)
  - Journal de travail complet
  - Export des VMs (optionnel selon taille)
  - Présentation de la stack en fonctionnement

---

## 9. POINTS TECHNIQUES ÉVALUÉS SPÉCIFIQUES AU PROJET

Le travail sera évalué sur les 7 points spécifiques suivants :

1. **Installation Proxmox** : L'hyperviseur Proxmox VE est correctement installé et configuré avec réseau et stockage fonctionnels.

2. **Architecture réseau** : Les VMs peuvent communiquer entre elles de manière sécurisée et fonctionnelle, avec une séparation logique appropriée.

3. **Services Docker** : Les containers Docker sont correctement configurés via docker-compose, avec gestion des variables d'environnement et des volumes persistants.

4. **Interconnexion fonctionnelle** : La stack complète fonctionne de bout en bout (reverse proxy → application → base de données) sans intervention manuelle.

5. **Sécurité de base** : Les bonnes pratiques de sécurité sont appliquées (mots de passe sécurisés, restriction d'accès réseau DB, pas de credentials en clair dans les fichiers).

6. **Documentation technique** : La documentation est complète, claire et permet à un tiers de reproduire l'installation. Les schémas d'architecture sont présents et pertinents.

7. **Gestion des snapshots** : Au moins un snapshot Proxmox est créé et la procédure de restauration est documentée.

---
