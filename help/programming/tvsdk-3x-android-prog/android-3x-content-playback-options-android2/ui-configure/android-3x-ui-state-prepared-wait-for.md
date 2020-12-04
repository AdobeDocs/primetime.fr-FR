---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
seo-description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: 7a86b4cf-f7a0-4d90-9ff2-401640a395c5
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---


# Attendre un état valide {#wait-for-a-valid-status}

Avec TVSDK, vous pouvez contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.

En attendant que le lecteur ait le bon état, vous avez la garantie que la ressource multimédia a bien été chargée. Si le lecteur n&#39;a pas au moins l&#39;état requis, de nombreuses méthodes du lecteur lancent `MediaPlayerException`.

L’état requis est généralement PRÉPARÉ. Dans ce cas, la routine de rappel pour `StatusChangeEventListener.onStatusChanged()` s&#39;exécute.

Pour confirmer que l’état est `PREPARED`, cochez `MediaPlayer.MediaPlayerStatus`.