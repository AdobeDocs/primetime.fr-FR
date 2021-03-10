---
description: Vous devrez peut-être savoir si le contenu multimédia est actif ou VOD.
title: Déterminer si le contenu est actif ou VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '85'
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

