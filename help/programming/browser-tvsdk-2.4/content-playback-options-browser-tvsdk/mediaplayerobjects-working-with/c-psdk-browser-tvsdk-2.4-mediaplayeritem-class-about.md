---
description: Une fois le chargement d’une ressource MediaResource réussi, le navigateur TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.
title: À propos de la classe MediaPlayerItem
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# À propos de la classe MediaPlayerItem{#about-the-mediaplayeritem-class}

Une fois le chargement d’une ressource MediaResource réussi, le navigateur TVSDK crée une instance de la classe MediaPlayerItem pour permettre l’accès à cette ressource.

La variable `MediaResource` représente une requête émise par la couche d’application à la variable `MediaPlayer` pour charger le contenu.

La variable `MediaPlayer` résout la ressource multimédia, charge le fichier de manifeste associé et analyse le manifeste. Il s’agit de la partie asynchrone du processus de chargement des ressources. La variable `MediaPlayerItem` est générée une fois la ressource résolue, et cette instance est une version résolue d’une `MediaResource`. Le SDK du navigateur permet d’accéder au nouveau `MediaPlayerItem` instance par `MediaPlayer.CurrentItem`.

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée avant d’accéder à l’élément du lecteur multimédia.
