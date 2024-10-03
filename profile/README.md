# MEDIC ASSIST - Mobile App & API 🦺

## Description

**Medic Assist** est une application mobile conçue pour suivre la localisation et les déplacements d'un patient dans son parcours de soin. Elle permet aux parties prenantes (médecins, proches, aidants, etc.) d'être informées en temps réel du statut du patient et de son avancement lors des rendez-vous médicaux. L'application inclut la gestion des rendez-vous, des notifications automatiques et la création de "bulles" qui regroupent les acteurs clés d'un acte médical.

### Fonctionnalités principales :
- Suivi de localisation du patient et notification des changements majeurs (départ domicile, arrivée à l'hôpital, etc.).
- Gestion des rendez-vous médicaux avec création automatique de "bulles" associées aux actes médicaux.
- Notifications de retard probable basées sur la géolocalisation et une estimation du temps de trajet.
- Rappel automatique de l'heure optimale de départ pour le patient.
- Simulation d'un planning de présence médicale pour divers services (scanner, consultation de suivi, etc.).
  
## Architecture du projet

L'application est composée de trois principales couches :

1. **Application Mobile (Kotlin)** : Suivi de localisation, gestion des rendez-vous, affichage des notifications, interaction avec les services de géolocalisation (OpenStreetMap, API de navigation).
2. **API Backend (Node.js)** : Gestion des bulles, des utilisateurs, des rendez-vous, et des notifications. Elle communique avec l'application mobile et la base de données pour fournir les données en temps réel.
3. **Base de Données (PostgreSQL)** : Stockage des informations liées aux utilisateurs, aux rendez-vous, à la localisation et aux notifications.

## Prérequis

Avant de pouvoir lancer ce projet, assurez-vous d'avoir les outils suivants installés :

- **Kotlin** pour l'application mobile.
- **Docker** et **Docker Compose** pour orchestrer l'API backend et la base de données.
- **Node.js** (version 14.x ou supérieure) pour l'API backend.
- **PostgreSQL** (version 12.x ou supérieure) pour la base de données.
- Une API de géolocalisation comme **OpenStreetMap** ou **Waze API**.

## Installation

### 1. Installation avec Docker Compose

Le projet utilise Docker Compose pour orchestrer l'API et PostgreSQL. Suivez ces étapes pour démarrer le backend.

Clonez le dépôt et allez dans le répertoire racine.

```bash
git clone https://github.com/Medic-Assist/api-project.git
cd api-project
docker-compose up --build
```

Créez un fichier .env à la racine avec vos configurations :


```bash
# Fichier .env
POSTGRES_USER=admin
POSTGRES_PASSWORD=secret
POSTGRES_DB=medic_assist_db
PORT=3000
```

Ensuite, démarrez les services Docker :

```bash

docker-compose up --build
```

Cela va démarrer :

    Un conteneur pour l'API backend en Node.js.
    Un conteneur pour PostgreSQL avec les variables définies dans .env.

    
2. Installation de l'application mobile (Kotlin)

Clonez le dépôt pour l'application mobile :

```bash

git clone https://github.com/medic-assist/application-mobile.git
```

Ouvrez le projet dans Android Studio et assurez-vous que toutes les dépendances sont correctement installées.

Compilez et exécutez l'application sur un émulateur ou un appareil physique.


## Fonctionnalités techniques
### Suivi de la localisation du patient

    Utilisation des services de géolocalisation pour suivre les déplacements du patient entre son domicile et le lieu du rendez-vous.
    Notifications envoyées automatiquement lors des étapes clés (départ, arrivée à l'hôpital, etc.).

### Gestion des bulles et des rendez-vous

    Création automatique d'une "bulle" pour chaque acte médical, regroupant le patient, les médecins, et d'autres acteurs pertinents.
    Notifications de retard basées sur une estimation du temps de trajet (calculée via OpenStreetMap ou une API tierce).

### Notifications automatiques

    Notification des membres de la bulle pour chaque étape clé du déplacement du patient.
    Estimation de retard basée sur le temps de trajet moyen et l'heure de départ prévue.

### Simulation des plannings médicaux

    Implémentation de deux services médicaux (Scanner et Consultation de suivi) avec des équipes médicales associées.
    Simulation de la présence médicale pour chaque type de rendez-vous.

### Points d'attention

    Optimisation des notifications pour éviter de notifier les membres non concernés.
    Utilisation d'API tierces (comme OpenStreetMap) pour la conversion des adresses en coordonnées géographiques.
    Gestion de la confidentialité et de la sécurité des données patient via des normes de sécurité strictes.

### Technologies utilisées

    Kotlin : pour le développement de l'application mobile Android.
    Node.js & Express : pour l'API backend.
    PostgreSQL : pour le stockage des données.
    Docker & Docker Compose : pour la gestion des conteneurs de l'API et de la base de données.
    OpenStreetMap API : pour la géolocalisation.
    Waze API : pour l'estimation du temps de trajet et des retards.

## Déploiement
### API Backend

L'API backend et la base de données peuvent être déployées sur tout environnement supportant Docker, comme AWS, DigitalOcean, ou Heroku. Vous pouvez aussi utiliser des services managés pour PostgreSQL.

### Application mobile
Distribuez l'application via Google Play ou un autre service de déploiement d'applications mobiles. N'oubliez pas de configurer les clés API pour la géolocalisation dans la version de production.


## Auteurs


Hett Alizée @dinholu - Développeur Fullstack, développeur mobile, cheffe de projet
Beaudeux Charline @charlineBx - Développeur mobile, développeur fullstack, Analyste
Baudry Baptiste @BdryBaptiste = Développeur mobile, développeur fullstack
Remy Nicolas @CFAI-Nicolas - Développeur mobile
Blaess Maxime @Koumaq - Développeur mobile
Brisson Jordan @LeSupaPoney - Développeur mobile, développeur front
Berard Ludovic @LudoPilot - Développeur fullstack
Shafizadeh Rashti Raha @@raha-sh - Développeur mobile, développeur fullstack, Analyste

