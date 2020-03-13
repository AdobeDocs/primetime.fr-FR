---
description: Une fois l’objet MediaResource chargé, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.
seo-description: Une fois l’objet MediaResource chargé, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.
seo-title: A propos de la classe MediaPlayerItem
title: A propos de la classe MediaPlayerItem
uuid: 2d37f358-d158-481b-81d5-27546e9c2e0e
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# A propos de la classe MediaPlayerItem {#about-the-mediaplayeritem-class}

L’objet MediaPlayer représente votre lecteur multimédia. Un objet MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.

Une fois l’objet MediaResource chargé, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.

Le `MediaResource` représente une requête émise par la couche d’application à l’ `MediaPlayer` instance pour charger le contenu.

Le `MediaPlayer` programme résout la ressource multimédia, charge le fichier manifeste associé et analyse le manifeste. Il s’agit de la partie asynchrone du processus de chargement des ressources. L’ `MediaPlayerItem` instance est générée une fois la ressource résolue, et cette instance est une version résolue d’une `MediaResource`. TVSDK permet d’accéder à l’ `MediaPlayerItem` instance nouvellement créée par le biais `MediaPlayer.CurrentItem`.

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée correctement avant d’accéder à l’élément du lecteur multimédia.