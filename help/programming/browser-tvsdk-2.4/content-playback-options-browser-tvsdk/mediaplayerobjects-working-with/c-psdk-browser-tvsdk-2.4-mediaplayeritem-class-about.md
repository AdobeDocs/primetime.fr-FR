---
description: Une fois que le chargement d’une ressource MediaResource a réussi, le navigateur TVSDK crée une instance de la classe MediaPlayerItem pour fournir un accès à cette ressource.
seo-description: Une fois que le chargement d’une ressource MediaResource a réussi, le navigateur TVSDK crée une instance de la classe MediaPlayerItem pour fournir un accès à cette ressource.
seo-title: A propos de la classe MediaPlayerItem
title: A propos de la classe MediaPlayerItem
uuid: 5226d3ad-2438-44fe-a8ef-bcc0da8331b8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# A propos de la classe MediaPlayerItem{#about-the-mediaplayeritem-class}

Une fois que le chargement d’une ressource MediaResource a réussi, le navigateur TVSDK crée une instance de la classe MediaPlayerItem pour fournir un accès à cette ressource.

Le `MediaResource` représente une requête émise par la couche d’application à l’ `MediaPlayer` instance pour charger le contenu.

Le `MediaPlayer` programme résout la ressource multimédia, charge le fichier manifeste associé et analyse le manifeste. Il s’agit de la partie asynchrone du processus de chargement des ressources. L’ `MediaPlayerItem` instance est générée une fois la ressource résolue, et cette instance est une version résolue d’une `MediaResource`. Le navigateur TVSDK permet d’accéder à l’ `MediaPlayerItem` instance nouvellement créée par le biais `MediaPlayer.CurrentItem`.

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée correctement avant d’accéder à l’élément du lecteur multimédia.

