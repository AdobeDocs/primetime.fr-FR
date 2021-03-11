---
description: TVSDK télécharge les segments d’annonce et les rend sur l’écran du périphérique.
title: Phase de lecture publicitaire
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Phase de lecture de la publicité{#ad-playback-phase}

TVSDK télécharge les segments d’annonce et les rend sur l’écran du périphérique.

À ce stade, TVSDK a résolu les publicités, les a placées sur la chronologie et tente de rendre le contenu à l’écran.

Les principales classes d&#39;erreurs suivantes peuvent se produire au cours de cette phase :

* Erreurs lors de la connexion au serveur hôte
* Erreurs lors du téléchargement du fichier manifeste
* Erreurs lors du téléchargement des segments de médias

Pour les trois classes d’erreur, TVSDK transmet les événements déclenchés à votre application, notamment :

* Événements de notification déclenchés en cas de basculement.
* La notification s’événement lorsque le profil est modifié en raison de l’algorithme de basculement.
* Événements de notification déclenchés lorsque toutes les options de basculement ont été prises en compte et qu&#39;aucune action supplémentaire ne peut être exécutée automatiquement.

   Votre application doit prendre les mesures appropriées.

Que des erreurs se produisent ou non, TVSDK appelle onAdBreakComplete pour chaque `onAdBreakStart` et `onAdComplete` pour chaque `onAdStart`. Cependant, si les segments n’ont pas pu être téléchargés, la chronologie peut présenter des lacunes. Lorsque les espaces sont suffisamment grands, les valeurs de la position du curseur de lecture et de la progression de la publicité signalée peuvent présenter des discontinuités.
