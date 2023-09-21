---
description: Toutes les requêtes d’insertion d’annonces utilisent la même structure d’URL et les mêmes paramètres de requête de base. Des paramètres de requête supplémentaires permettent au serveur de manifeste de fonctionner avec divers clients et situations.
title: Demandes d’insertion de publicités
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Demandes d’insertion de publicités {#requests-for-ad-insertion}

Toutes les requêtes d’insertion d’annonces utilisent la même structure d’URL et les mêmes paramètres de requête de base. Des paramètres de requête supplémentaires permettent au serveur de manifeste de fonctionner avec divers clients et situations.

| Paramètre | Description |
|--- |--- |
| u | L’ID de ressource est un hachage MD5 de ad_request_id provenant des métadonnées de prise de décision publicitaire d’Adobe Primetime. Fourni par le gestionnaire de compte technique de votre Adobe. |
| z | ID de zone de la ressource qui doit être fournie à Auditude. Fourni par le gestionnaire de compte technique de votre Adobe. |
| `__sid__` | Identifiant unique que le serveur de manifeste utilisera pour générer l’identifiant de session. |

>[!NOTE]
>
>La variable `__sid__` est entouré de caractères de soulignement doubles.

Le serveur de manifeste conserve les sessions pour des clients individuels ou des groupes de clients afin de s’assurer que les séquences d’interactions API pour différents clients restent séparées. La variable `__sid__` que le client envoie dans l’URL de bootstrap au serveur manifest doit être unique dans son environnement. Le serveur de manifeste l’utilise pour construire un identifiant unique global, qu’il renvoie au client.

Les autres paramètres de requête concernent différents clients et situations.