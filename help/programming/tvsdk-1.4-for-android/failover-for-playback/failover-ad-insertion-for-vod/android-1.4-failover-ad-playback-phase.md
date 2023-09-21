---
description: TVSDK télécharge les segments d’annonce et les affiche sur l’écran de l’appareil.
title: Phase de lecture de la publicité
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Phase de lecture de la publicité{#ad-playback-phase}

TVSDK télécharge les segments d’annonce et les affiche sur l’écran de l’appareil.

À ce stade, TVSDK a résolu les publicités, les a placées dans la chronologie et tente d’afficher le contenu à l’écran.

Les principales classes d&#39;erreurs suivantes peuvent se produire dans cette phase :

* Erreurs lors de la connexion au serveur hôte
* Erreurs lors du téléchargement du fichier manifeste
* Erreurs lors du téléchargement des segments multimédia

Pour les trois classes d’erreur, TVSDK transmet les événements déclenchés à votre application, notamment :

* Événements de notification déclenchés en cas de basculement.
* Événements de notification lorsque le profil est modifié en raison de l’algorithme de basculement.
* Événements de notification déclenchés lorsque toutes les options de basculement ont été prises en compte et qu’aucune action supplémentaire ne peut être effectuée automatiquement.

  Votre application doit prendre les mesures appropriées.

Que des erreurs se soient produites ou non, TVSDK appelle onAdBreakComplete pour chaque événement `onAdBreakStart` et `onAdComplete` pour chaque `onAdStart`. Toutefois, si les segments n’ont pas pu être téléchargés, la chronologie peut présenter des lacunes. Lorsque les espaces sont suffisamment grands, les valeurs de la position du curseur de lecture et la progression de la publicité signalée peuvent présenter des discontinuités.
