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

- Un serveur physique ou VM puissante pour installer Proxmox VE
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

### Exemple de stack suggérée

**VM1 - Reverse Proxy**
- Nginx ou Traefik en container Docker
- Gestion du routage vers les autres services

**VM2 - Application**
- Application web (Node.js, Python, PHP, etc.) en container
- Communique avec la base de données sur VM3

**VM3 - Base de données**
- PostgreSQL, MySQL ou MongoDB en container
- Accessible uniquement depuis VM2 (sécurité réseau)

---

## 7. ÉTAPES DU PROJET

### Jour 1 - Installation et configuration de base

**Étape 1 : Installation Proxmox VE**
- Installer Proxmox VE sur le serveur
- Configuration initiale (réseau, stockage, updates)
- Accès interface web et configuration sécurité de base

**Étape 2 : Planification de l'infrastructure**
- Définir l'architecture réseau
- Planifier la répartition des ressources (CPU, RAM, disque)
- Définir la stack applicative à déployer

**Étape 3 : Création des VMs/Containers**
- Créer 2-3 VMs Ubuntu Server ou containers LXC
- Configuration réseau de chaque VM
- Installation de Docker et docker-compose sur chaque instance
- Test de connectivité entre les VMs

### Jour 2 - Déploiement des services Docker

**Étape 4 : Configuration du reverse proxy (VM1)**
- Déployer Nginx ou Traefik via Docker
- Configuration des routes vers les autres services
- Mise en place des certificats SSL (self-signed acceptable)

**Étape 5 : Déploiement de l'application (VM2)**
- Choisir et déployer une application web simple
- Configuration docker-compose
- Variables d'environnement pour connexion base de données
- Test local de l'application

**Étape 6 : Déploiement de la base de données (VM3)**
- Déployer PostgreSQL/MySQL/MongoDB via Docker
- Configuration sécurité (restriction accès réseau)
- Création de la base et utilisateur pour l'application
- Test de connexion depuis VM2

**Étape 7 : Interconnexion des services**
- Vérifier la communication entre tous les services
- Tester le flux complet : Reverse Proxy → App → DB
- Résolution des problèmes de connectivité
- Validation fonctionnelle de la stack complète

### Jour 3 - Tests, optimisation et documentation

**Étape 8 : Tests et validation**
- Tests fonctionnels complets de la stack
- Vérification des logs de chaque service
- Test de résilience (redémarrage d'un service)
- Validation des performances de base

**Étape 9 : Snapshots et backup**
- Création de snapshots Proxmox des VMs
- Documentation de la procédure de backup
- Test de restauration d'un snapshot

**Étape 10 : Documentation complète**
- Architecture et schémas réseau
- Procédure d'installation pas à pas
- Configuration de chaque service
- Fichiers docker-compose documentés
- Procédures de troubleshooting
- README.md structuré

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

## 10. VALIDATION

| | Lu et approuvé le : | Signature : |
|---|---|---|
| **Candidat** : | | |
| **Chef de projet** : | | |

---

## ANNEXE : Suggestions d'applications

Si tu manques d'idées pour la stack applicaative, voici quelques suggestions :

**Option 1 - Blog WordPress(moyen)**
- VM1 : Nginx reverse proxy
- VM2 : WordPress (PHP + Apache)
- VM3 : MySQL

**Option 2 - Stack Node.js**
- VM1 : Traefik reverse proxy
- VM2 : Application Node.js (Express + React)
- VM3 : MongoDB

**Option 3 - Monitoring**
- VM1 : Nginx + Grafana
- VM2 : Prometheus
- VM3 : Base de données TimeSeries

Tu es libre de choisir ta stack, mais tu dois me la valider jour 1.
