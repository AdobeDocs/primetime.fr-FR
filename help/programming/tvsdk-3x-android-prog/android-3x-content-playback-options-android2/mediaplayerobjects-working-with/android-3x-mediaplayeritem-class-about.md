---
description: Une fois l’objet MediaResource chargé, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.
seo-description: Une fois l’objet MediaResource chargé, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.
seo-title: A propos de la classe MediaPlayerItem
title: A propos de la classe MediaPlayerItem
uuid: fc79c442-2e38-48c4-8ef9-6dce9ad6790a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# A propos de la classe MediaPlayerItem {#about-the-mediaplayeritem-class}

L’objet MediaPlayer représente votre lecteur multimédia. Un objet MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.

Une fois l’objet MediaResource chargé, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.

Le `MediaResource` représente une requête émise par la couche d’application à l’ `MediaPlayer` instance pour charger le contenu.

Le `MediaPlayer` programme résout la ressource multimédia, charge le fichier manifeste associé et analyse le manifeste. Il s’agit de la partie asynchrone du processus de chargement des ressources. L’ `MediaPlayerItem` instance est générée une fois la ressource résolue, et cette instance est une version résolue d’une `MediaResource`. TVSDK permet d’accéder à l’ `MediaPlayerItem` instance nouvellement créée par le biais `MediaPlayer.CurrentItem`.

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée correctement avant d’accéder à l’élément du lecteur multimédia.