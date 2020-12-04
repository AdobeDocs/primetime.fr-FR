---
description: L’objet MediaPlayer représente votre lecteur multimédia. Un MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.
seo-description: L’objet MediaPlayer représente votre lecteur multimédia. Un MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.
seo-title: A propos de la classe MediaPlayerItem
title: A propos de la classe MediaPlayerItem
uuid: d7f65edf-4693-4b1e-bae0-46fadce98751
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# A propos de la classe MediaPlayerItem{#about-the-mediaplayeritem-class}

L’objet MediaPlayer représente votre lecteur multimédia. Un MediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.

Une fois qu’une ressource multimédia a été chargée, TVSDK crée une instance de la classe `MediaPlayerItem` afin de fournir l’accès à cette ressource.

`MediaResource` représente une requête émise par la couche d&#39;application à l&#39;instance `MediaPlayer` pour charger le contenu.

`MediaPlayer` résout la ressource média, charge le fichier manifeste associé et analyse le manifeste. Il s&#39;agit de la partie asynchrone du processus de chargement des ressources. L&#39;instance `MediaPlayerItem` est générée après la résolution de la ressource, et cette instance est une version résolue d&#39;une `MediaResource`. TVSDK permet d’accéder à l’instance `MediaPlayerItem` nouvellement créée par `MediaPlayer.CurrentItem`

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée correctement avant d&#39;accéder à l&#39;élément du lecteur multimédia.

