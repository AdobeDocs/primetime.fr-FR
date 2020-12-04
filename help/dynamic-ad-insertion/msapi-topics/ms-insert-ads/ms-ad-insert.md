---
description: Toutes les requêtes d’insertion publicitaire utilisent la même structure d’URL et les mêmes paramètres de requête de base. Des paramètres de requête supplémentaires permettent au serveur de manifeste de fonctionner avec divers clients et situations.
seo-description: Toutes les requêtes d’insertion publicitaire utilisent la même structure d’URL et les mêmes paramètres de requête de base. Des paramètres de requête supplémentaires permettent au serveur de manifeste de fonctionner avec divers clients et situations.
seo-title: Demandes d’insertion de publicités
title: Demandes d’insertion de publicités
uuid: e42b3228-bff7-4202-86ed-7f631f3016ae
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# Demandes d&#39;insertion de publicité {#requests-for-ad-insertion}

Toutes les requêtes d’insertion publicitaire utilisent la même structure d’URL et les mêmes paramètres de requête de base. Des paramètres de requête supplémentaires permettent au serveur de manifeste de fonctionner avec divers clients et situations.

| Paramètre | Description |
|--- |--- |
| u | L’ID de ressource est un hachage MD5 de l’ID ad_request_id provenant des métadonnées de prise de décision publicitaire Adobe Primetime. Fourni par votre gestionnaire de compte technique Adobe. |
| z | ID de zone de la ressource qui doit être fournie à Auditude. Fourni par votre gestionnaire de compte technique Adobe. |
| `__sid__` | Identifiant unique que le serveur de manifeste utilisera pour générer l&#39;identifiant de session. |

>[!NOTE]
>
>Le paramètre `__sid__` est entouré de caractères de soulignement doublon.

Le serveur de manifeste gère des sessions pour des clients individuels ou des groupes de clients afin de s’assurer que les séquences d’interactions d’API pour différents clients restent séparées. Le `__sid__` que le client envoie dans l&#39;URL d&#39;amorçage au serveur de manifeste doit être unique dans son environnement. Le serveur de manifeste l’utilise pour construire un identifiant unique global, qu’il renvoie au client.

Les autres paramètres de requête concernent différents clients et différentes situations.