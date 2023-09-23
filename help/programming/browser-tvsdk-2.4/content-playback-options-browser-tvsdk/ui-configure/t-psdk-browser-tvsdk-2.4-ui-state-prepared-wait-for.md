---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur Browser TVSDK, le lecteur doit être dans un état valide.
title: Attente d’un état valide
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Attente d’un état valide {#wait-for-a-valid-state}

Avant de pouvoir utiliser la plupart des méthodes du lecteur Browser TVSDK, le lecteur doit être dans un état valide.

Le lecteur se déplace à travers différents états. En attendant que le lecteur se trouve dans l’état correct, vérifiez que la ressource multimédia a bien été chargée. Si le lecteur n’est pas dans l’état requis au moins, de nombreuses méthodes du lecteur sont lancées `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.

1. Pour confirmer que l’état est PRÉPARÉ :

   Lorsque le lecteur est en cours d’initialisation, attendez que le navigateur TVSDK distribue le `AdobePSDK.MediaPlayerStatusChangeEvent` avec un événement `event.status` de `MediaPlayerStatus.PREPARED`.

   Pour vérifier si l’état actuel de l’objet MediaPlayer est au moins PRÉPARÉ.

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```
