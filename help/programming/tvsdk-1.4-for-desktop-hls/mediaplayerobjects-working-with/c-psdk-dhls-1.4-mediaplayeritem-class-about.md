---
description: L’objet MediaPlayer représente votre lecteur multimédia. Un objet MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.
seo-description: L’objet MediaPlayer représente votre lecteur multimédia. Un objet MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.
seo-title: A propos de la classe MediaPlayerItem
title: A propos de la classe MediaPlayerItem
uuid: 531dd1a6-d72c-4ae3-9c3f-2f1d854245c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# A propos de la classe MediaPlayerItem{#about-the-mediaplayeritem-class}

L’objet MediaPlayer représente votre lecteur multimédia. Un objet MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.

<!--<a id="section_01BC89E5C5A94D0A95EF9D29FBCE758A"></a>-->

Une fois qu’une ressource multimédia a été chargée, TVSDK crée une instance de la `MediaPlayerItem` classe pour fournir un accès à cette ressource.

Le `MediaResource` représente une requête émise par la couche d’application à l’ `MediaPlayer` instance pour charger le contenu.

Le `MediaPlayer` programme résout la ressource multimédia, charge le fichier manifeste associé et analyse le manifeste. Il s’agit de la partie asynchrone du processus de chargement des ressources. L’ `MediaPlayerItem` instance est générée une fois la ressource résolue, et cette instance est une version résolue d’une `MediaResource`. TVSDK permet d’accéder à l’ `MediaPlayerItem` instance nouvellement créée par le biais `MediaPlayer.currentItem`.

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée correctement avant d’accéder à l’élément du lecteur multimédia.

