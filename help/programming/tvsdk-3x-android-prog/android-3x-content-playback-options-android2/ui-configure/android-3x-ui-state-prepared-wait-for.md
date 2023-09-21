---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit disposer d’un état valide.
title: Attente d’un état valide
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Attente d’un état valide {#wait-for-a-valid-status}

Avec TVSDK, vous pouvez contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit disposer d’un état valide.

En attendant que le lecteur soit dans le bon état, vous avez la garantie que la ressource multimédia a bien été chargée. Si le lecteur n’est pas au moins dans l’état requis, de nombreuses méthodes du lecteur sont lancées `MediaPlayerException`.

L’état requis est généralement PRÉPARÉ. Dans ce cas, la routine de rappel pour `StatusChangeEventListener.onStatusChanged()` s’exécute.

Pour confirmer que l’état est `PREPARED`, cochez `MediaPlayer.MediaPlayerStatus`.
