---
description: Toutes les requêtes d’insertion d’annonces publicitaires utilisent la même structure d’URL et les mêmes paramètres de base de . Des paramètres  supplémentaires permettent au serveur de manifeste de fonctionner avec divers clients et situations.
seo-description: Toutes les requêtes d’insertion d’annonces publicitaires utilisent la même structure d’URL et les mêmes paramètres de base de . Des paramètres  supplémentaires permettent au serveur de manifeste de fonctionner avec divers clients et situations.
seo-title: Demandes d’insertion de publicités
title: Demandes d’insertion de publicités
uuid: e42b3228-bff7-4202-86ed-7f631f3016ae
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Demandes d’insertion de publicités {#requests-for-ad-insertion}

Toutes les requêtes d’insertion d’annonces publicitaires utilisent la même structure d’URL et les mêmes paramètres de base de . Des paramètres  supplémentaires permettent au serveur de manifeste de fonctionner avec divers clients et situations.

| Paramètre | Description |
|--- |--- |
| u | L’ID de ressource est un hachage MD5 de ad_request_id issu des métadonnées de prise de décision publicitaire Adobe Primetime. Fourni par votre gestionnaire de compte technique Adobe. |
| z | ID de zone de la ressource qui doit être fournie à Auditude. Fourni par votre gestionnaire de compte technique Adobe. |
| `__sid__` | ID unique que le serveur de manifeste utilisera pour générer l’ID de session. |

>[!NOTE]
>
>Le `__sid__` paramètre est entouré de caractères de soulignement .

Le serveur de manifeste gère des sessions pour des clients individuels ou des groupes de clients afin de garantir que les séquences d’interactions API pour différents clients restent distinctes. Le `__sid__` que le client envoie dans l’URL d’amorçage au serveur de manifeste doit être unique dans son  de . Le serveur de manifeste l’utilise pour construire un identifiant unique global, qu’il renvoie au client.

Les autres paramètres de  du concernent différents clients et différentes situations.