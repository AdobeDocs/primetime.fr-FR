---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur Browser TVSDK, le lecteur doit être dans un état valide.
title: Attendre un état valide
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Attendre un état {#wait-for-a-valid-state} valide

Avant de pouvoir utiliser la plupart des méthodes du lecteur Browser TVSDK, le lecteur doit être dans un état valide.

Le joueur se déplace à travers différents états. En attendant que le lecteur soit à l’état correct, vous avez la garantie que la ressource multimédia a été chargée avec succès. Si le lecteur n&#39;est pas dans l&#39;état requis au moins, de nombreuses méthodes du lecteur lancent `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.

1. Pour confirmer que l’état est PRÉPARÉ :

   Une fois le lecteur initialisé, attendez que le navigateur TVSDK distribue le événement `AdobePSDK.MediaPlayerStatusChangeEvent` avec un `event.status` de `MediaPlayerStatus.PREPARED`.

   Pour vérifier si l’état actuel de l’objet MediaPlayer est au moins PRÉPARÉ.

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```

