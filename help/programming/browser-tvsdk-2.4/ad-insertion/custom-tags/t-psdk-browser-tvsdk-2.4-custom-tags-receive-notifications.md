---
description: Pour recevoir des notifications concernant les balises dans le manifeste, écoutez AdobePSDK.TimedMetadataEvent.
seo-description: Pour recevoir des notifications concernant les balises dans le manifeste, écoutez AdobePSDK.TimedMetadataEvent.
seo-title: Ajouter des écouteurs pour les notifications de métadonnées minutées
title: Ajouter des écouteurs pour les notifications de métadonnées minutées
uuid: c82c5549-0ab6-4343-a766-5176e784d4cb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# Ajouter des écouteurs pour les notifications de métadonnées minutées{#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications concernant les balises dans le manifeste, écoutez AdobePSDK.TimedMetadataEvent.

Lorsqu’un nouvel objet `TimedMetadata` est créé, MediaPlayer distribue `AdobePSDK.TimedMetadataEvent`.

1. Mettez en oeuvre les écouteurs appropriés.

   ```js
   function onTimedMetadataEvent(event) { 
       var timedMetadata = event.timedMetadata; 
       // process the timed metadata collection 
       } 
   ```

1. Enregistrez les écouteurs de événement.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE, onTimedMetadataEvent);
   ```

Les métadonnées ID3 sont distribuées via le même `Events.TimedMetadataEvent`. Vous pouvez utiliser la propriété `timedMetadata.type` pour distinguer la balise TAG de l&#39;ID3.

