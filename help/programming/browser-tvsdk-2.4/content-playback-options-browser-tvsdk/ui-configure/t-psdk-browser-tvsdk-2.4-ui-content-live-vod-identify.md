---
description: Vous devrez peut-être savoir si le contenu multimédia est actif ou VOD.
title: Déterminer si le contenu est actif ou VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---

# Déterminer si le contenu est actif ou VOD{#identify-whether-the-content-is-live-or-vod}

Vous devrez peut-être savoir si le contenu multimédia est actif ou VOD.

1. Attendez que le SDK du navigateur déclenche une `AdobePSDK.PSDKEventType.STATUS_CHANGED` avec un événement `event.status` de `AdobePSDK.MediaPlayerStatus.PREPARED`.

   Cette étape permet de s’assurer que la ressource multimédia a bien été chargée.

   >[!IMPORTANT]
   >
   >Si Browser TVSDK n’est pas dans au moins la variable `PREPARED` La tentative d’appel des méthodes suivantes renvoie une `IllegalStateException`.

1. Lecture `live` de la `MediaPlayerItem` interface :

   ```js
   player.currentItem.live
   ```
