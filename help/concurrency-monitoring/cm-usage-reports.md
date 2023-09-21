---
title: Rapports d’utilisation de surveillance de la simultanéité
description: Rapports d’utilisation de surveillance de la simultanéité
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# Rapports d’utilisation de surveillance de la simultanéité {#cm-usage-reports}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.



## Présentation {#usage-rep-overview}

La variable **Rapports d’utilisation de surveillance de la simultanéité** Le service est disponible via une API REST qui fournit des informations sur l’utilisation simultanée comme indiqué par les applications du client.

## Conditions préalables {#usage-rep-prerequisites}

Pour accéder au produit Rapports d’utilisation de surveillance de la simultanéité , un client doit d’abord contacter la surveillance de la simultanéité . [Équipe d’assistance](mailto:tve-support@adobe.com) et ils exécuteront les étapes nécessaires pour vous permettre d’accéder au produit API.

## Mesures et ventilations des rapports généraux {#general-rep-metrics-breakdown}

### Les utilisateurs des rapports d’utilisation peuvent surveiller les mesures suivantes :{#monitor-metrics}

| Nom | Description |
|:---|:---|
| active-users | nombre de comptes d’utilisateurs distincts ayant lancé au moins une session de diffusion en continu au cours de l’intervalle, ventilés par granularité temporelle |
| active-sessions | nombre de sessions en continu ayant signalé une activité au cours de l’intervalle (il n’inclut pas les tentatives ayant échoué, les sessions ayant reçu une réponse de refus pour l’appel d’initialisation). |
| started-sessions | nombre de sessions en continu démarrées dans l’intervalle |
| completed-sessions | nombre de sessions en continu terminées au cours de l’intervalle (explicitement ou en raison du délai d’expiration) |
| failed-tries | nombre de tentatives d’initialisation de session qui ont reçu une réponse de refus |
| non-sessions | nombre de sessions en continu qui ont été terminées pendant la lecture (sur pulsation) en raison d’une violation de politique. Cette mesure n’a de sens que lorsqu’une stratégie FIFO ou last_one_wins est mise en oeuvre. |
| kill-sessions | Nombre de sessions en continu qui ont été explicitement tuées au démarrage d’une nouvelle session (via l’en-tête X-Terminate) |
| duration_0-15 | nombre de diffusions d’une durée comprise entre 0 et 15 minutes |
| duration_15-30 | nombre de diffusions d’une durée comprise entre 15 et 30 minutes |
| duration_30-60 | nombre de diffusions d’une durée comprise entre 30 et 60 minutes |
| duration_60-120 | nombre de diffusions d’une durée comprise entre 60 et 120 minutes |
| duration_2h-4h | nombre de diffusions d’une durée comprise entre 2 heures (120 minutes) et 4 heures |
| duration_4h-8h | nombre de diffusions d’une durée comprise entre 4 heures et 8 heures |
| duration_8h-16h | nombre de diffusions d’une durée comprise entre 8 heures et 16 heures |
| duration_16h-1d | nombre de diffusions d’une durée comprise entre 16 heures et 1 jour (24 heures) |
| duration_1d-3d | nombre de diffusions d’une durée comprise entre 1 jour et 3 jours |
| duration_3d-7d | nombre de diffusions d’une durée comprise entre 3 jours et 7 jours |
| duration_1w-1m | nombre de diffusions d’une durée comprise entre 1 semaine (7 jours) et 1 mois (30 jours) |
| duration_over-1m | nombre de diffusions d’une durée supérieure à 1 mois (30 jours) |

### Les utilisateurs des rapports d’utilisation peuvent filtrer les mesures répertoriées ci-dessus selon les dimensions suivantes : {#dimensions-2-filter-metrics}

| Nom de la Dimension | Description |
|:---|:---|
| year | Année à 4 chiffres |
| month | Mois de l’année (1-12) |
| day | Jour du mois (1-31) |
| hour | Heure de la journée |
| minute | La minute de l’heure |
| application | Nom de l’application enregistré dans la surveillance simultanée utilisée pour gérer les sessions |
| application-id | ID d’application enregistré dans la surveillance de la simultanéité utilisé pour gérer les sessions |
| channel | Métadonnées de canal envoyées lors de l’initialisation de la session (marquées comme Inconnues si aucune métadonnée n’est envoyée) |
| mvpd | MVPD fourni lors de la gestion des sessions |
| platform | Métadonnées de plateforme fournies lors de l’initialisation de session ou prédéfinies pour une application au niveau de la configuration |

## Mesures et ventilations des rapports simultanés {#concurrency-reports-metrics-breakdown}

À compter de la version 2.9.0 de la surveillance de la simultanéité, nous avons introduit un nouveau rapport pour comprendre l’utilisation simultanée : un histogramme pour **niveau d’accès simultané** et **niveau d’activité**.

Le principal objectif de ce rapport est de vous aider à comprendre l’impact de la définition d’une stratégie avec une certaine limite de simultanéité et de vous donner suffisamment d’informations pour décider si vous devez augmenter la limite.

### Les utilisateurs des rapports d’utilisation peuvent surveiller les mesures suivantes : {#metrics-usage-rep-users}

| Nom de la Dimension | Description |
|:---|:---|
| utilisateurs | nombre d’utilisateurs ayant atteint chaque niveau d’accès simultané/d’activité |

### Les utilisateurs des rapports d’utilisation peuvent filtrer les mesures répertoriées ci-dessus selon les dimensions suivantes : {#dimensions-to-filter-metrics}

| Nom de la Dimension | Description |
|:---|:---|
| year | Année à 4 chiffres |
| month | Mois de l’année (1-12) |
| day | Jour du mois (1-31) |
| niveau d’accès simultané | Représente n’importe quel **activité de flux qui a été approuvée lors de la phase d’initialisation de la session** pour un utilisateur afin de pouvoir observer combien de flux simultanés **ouvert** par un utilisateur et pour comprendre l’impact de l’application d’une certaine limite de simultanéité |
| niveau d’activité | Représente n’importe quel **activité de diffusion (quel que soit son état : démarrée, active, arrêtée, rejetée)** pour un utilisateur afin de pouvoir observer combien de flux simultanés un utilisateur a tenté d’ouvrir et de comprendre l’impact de l’application d’une certaine limite de simultanéité |
| mvpd | MVPD fourni lors de la gestion des sessions |