---
description: TVSDK télécharge les segments d’annonce et les rend sur l’écran du périphérique.
seo-description: TVSDK télécharge les segments d’annonce et les rend sur l’écran du périphérique.
seo-title: Phase de lecture publicitaire
title: Phase de lecture publicitaire
uuid: 1bbcea08-3475-4a64-9f89-c455d5dd828e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Phase de lecture publicitaire{#ad-playback-phase}

TVSDK télécharge les segments d’annonce et les rend sur l’écran du périphérique.

À ce stade, TVSDK a résolu les publicités, les a placées sur la chronologie et tente de rendre le contenu à l’écran.

Les principales classes d&#39;erreurs suivantes peuvent se produire au cours de cette phase :

* Erreurs lors de la connexion au serveur hôte
* Erreurs lors du téléchargement du fichier manifeste
* Erreurs lors du téléchargement des segments de médias

Pour les trois classes d’erreur, TVSDK transmet les événements déclenchés à votre application, notamment :

* événements de notification déclenchés en cas de basculement.
* La notification s’événement lorsque le profil est modifié en raison de l’algorithme de basculement.
* événements de notification déclenchés lorsque toutes les options de basculement ont été prises en compte et qu&#39;aucune action supplémentaire ne peut être exécutée automatiquement.

   Votre application doit prendre les mesures appropriées.

Que des erreurs se produisent ou non, TVSDK appelle onAdBreakComplete pour chaque `onAdBreakStart` et `onAdComplete` pour chaque `onAdStart`variable. Cependant, si les segments n’ont pas pu être téléchargés, la chronologie peut présenter des lacunes. Lorsque les espaces sont suffisamment grands, les valeurs de la position du curseur de lecture et de la progression de la publicité signalée peuvent présenter des discontinuités.
