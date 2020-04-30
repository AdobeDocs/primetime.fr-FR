---
description: Après avoir chargé l’objet MediaResource, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.
seo-description: Après avoir chargé l’objet MediaResource, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.
seo-title: A propos de la classe MediaPlayerItem
title: A propos de la classe MediaPlayerItem
uuid: 2d37f358-d158-481b-81d5-27546e9c2e0e
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# A propos de la classe MediaPlayerItem {#about-the-mediaplayeritem-class}

L’objet MediaPlayer représente votre lecteur multimédia. Un MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.

Après avoir chargé l’objet MediaResource, TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.

Le `MediaResource` représente une requête émise par la couche d’application à l’ `MediaPlayer` instance pour charger le contenu.

Le `MediaPlayer` résout la ressource média, charge le fichier manifeste associé et analyse le manifeste. Il s&#39;agit de la partie asynchrone du processus de chargement des ressources. L&#39; `MediaPlayerItem` instance est générée après la résolution de la ressource, et cette instance est une version résolue d&#39;une `MediaResource`instance. TVSDK permet d’accéder à l’ `MediaPlayerItem` instance nouvellement créée par le biais `MediaPlayer.CurrentItem`.

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée correctement avant d&#39;accéder à l&#39;élément du lecteur multimédia.