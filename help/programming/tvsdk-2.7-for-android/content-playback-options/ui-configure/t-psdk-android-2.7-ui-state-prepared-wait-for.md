---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.
seo-description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: ffa63ad6-84d3-4eb2-aa99-026418d86528
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Attendre un état valide {#wait-for-a-valid-state}

Avec TVSDK, vous pouvez contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.

En attendant que le lecteur soit dans le bon état, vous assurez que la ressource multimédia a bien été chargée. Si le lecteur n’est pas au moins dans l’état requis, de nombreuses méthodes du lecteur sont renvoyées `MediaPlayerException`.

L’état requis est généralement PRÉPARÉ. Dans ce cas, la routine de rappel pour `StatusChangeEventListener.onStatusChanged()` s’exécute.

1. Pour confirmer que l’état est `PREPARED`, cochez `MediaPlayer.MediaPlayerStatus`.
