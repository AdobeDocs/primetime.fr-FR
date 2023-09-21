---
description: Pour recevoir des notifications sur les balises dans le manifeste, écoutez AdobePSDK.TimedMetadataEvent.
title: Ajout d’écouteurs pour les notifications de métadonnées minutées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# Ajout d’écouteurs pour les notifications de métadonnées minutées{#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur les balises dans le manifeste, écoutez AdobePSDK.TimedMetadataEvent.

Lorsqu’une nouvelle `TimedMetadata` est créé, le lecteur multimédia distribue `AdobePSDK.TimedMetadataEvent`.

1. Mettez en oeuvre les écouteurs appropriés.

   ```js
   function onTimedMetadataEvent(event) { 
       var timedMetadata = event.timedMetadata; 
       // process the timed metadata collection 
       } 
   ```

1. Enregistrez les écouteurs d’événement.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE, onTimedMetadataEvent);
   ```

Les métadonnées ID3 sont distribuées par le biais de la même `Events.TimedMetadataEvent`. Vous pouvez utiliser la variable `timedMetadata.type` pour faire la distinction entre TAG et ID3.
