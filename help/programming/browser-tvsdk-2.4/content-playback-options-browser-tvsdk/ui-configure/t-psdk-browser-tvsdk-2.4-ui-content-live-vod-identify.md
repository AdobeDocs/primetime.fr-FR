---
description: Vous devrez peut-être savoir si le contenu multimédia est en direct ou VOD.
seo-description: Vous devrez peut-être savoir si le contenu multimédia est en direct ou VOD.
seo-title: Déterminer si le contenu est actif ou VOD
title: Déterminer si le contenu est actif ou VOD
uuid: 5455801e-b5eb-4829-bde6-ef4440cd69c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Déterminer si le contenu est actif ou VOD{#identify-whether-the-content-is-live-or-vod}

Vous devrez peut-être savoir si le contenu multimédia est en direct ou VOD.

1. Attendez que le navigateur TVSDK déclenche un `AdobePSDK.PSDKEventType.STATUS_CHANGED` avec un `event.status` nombre de `AdobePSDK.MediaPlayerStatus.PREPARED`.

   Cette étape permet de s’assurer que la ressource multimédia a bien été chargée.

   >[!IMPORTANT]
   >
   >Si le navigateur TVSDK n’est pas dans l’ `PREPARED` état, la tentative d’appel des méthodes suivantes renvoie une valeur `IllegalStateException`.

1. Lecture `live` à partir de l’ `MediaPlayerItem` interface :

   ```js
   player.currentItem.live
   ```

