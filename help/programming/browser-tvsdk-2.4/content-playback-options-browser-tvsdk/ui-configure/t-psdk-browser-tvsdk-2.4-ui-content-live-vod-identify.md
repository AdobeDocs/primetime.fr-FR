---
description: Vous devrez peut-être savoir si le contenu multimédia est actif ou VOD.
seo-description: Vous devrez peut-être savoir si le contenu multimédia est actif ou VOD.
seo-title: Déterminer si le contenu est actif ou VOD
title: Déterminer si le contenu est actif ou VOD
uuid: 5455801e-b5eb-4829-bde6-ef4440cd69c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Déterminer si le contenu est actif ou VOD{#identify-whether-the-content-is-live-or-vod}

Vous devrez peut-être savoir si le contenu multimédia est actif ou VOD.

1. Attendez que le navigateur TVSDK déclenche un événement `AdobePSDK.PSDKEventType.STATUS_CHANGED` avec un `event.status` de `AdobePSDK.MediaPlayerStatus.PREPARED`.

   Cette étape permet de s’assurer que le chargement de la ressource multimédia a réussi.

   >[!IMPORTANT]
   >
   >Si le navigateur TVSDK n’est pas à au moins l’état `PREPARED`, la tentative d’appel des méthodes suivantes renvoie une valeur `IllegalStateException`.

1. Lisez `live` à partir de l&#39;interface `MediaPlayerItem` :

   ```js
   player.currentItem.live
   ```

