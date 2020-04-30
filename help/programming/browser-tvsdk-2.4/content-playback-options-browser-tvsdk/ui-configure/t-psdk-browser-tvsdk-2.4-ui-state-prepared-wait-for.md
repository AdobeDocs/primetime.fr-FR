---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur Browser TVSDK, le lecteur doit être dans un état valide.
seo-description: Avant de pouvoir utiliser la plupart des méthodes du lecteur Browser TVSDK, le lecteur doit être dans un état valide.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: 0add29a8-fbd8-483a-8c99-e4bc6de9e3d3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Attendre un état valide {#wait-for-a-valid-state}

Avant de pouvoir utiliser la plupart des méthodes du lecteur Browser TVSDK, le lecteur doit être dans un état valide.

Le joueur se déplace à travers différents états. En attendant que le lecteur soit à l’état correct, vous avez la garantie que la ressource multimédia a été chargée avec succès. Si le lecteur n&#39;est pas dans l&#39;état requis, de nombreuses méthodes du lecteur sont lancées `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.

1. Pour confirmer que l’état est PRÉPARÉ :

   Lorsque le lecteur est en cours d’initialisation, attendez que le navigateur TVSDK distribue le `AdobePSDK.MediaPlayerStatusChangeEvent` événement avec un `event.status` de `MediaPlayerStatus.PREPARED`.

   Pour vérifier si l’état actuel de l’objet MediaPlayer est au moins PRÉPARÉ.

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```

