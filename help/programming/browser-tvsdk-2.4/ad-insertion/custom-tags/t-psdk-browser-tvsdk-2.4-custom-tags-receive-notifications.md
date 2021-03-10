---
description: Pour recevoir des notifications concernant les balises dans le manifeste, écoutez AdobePSDK.TimedMetadataEvent.
title: Ajouter des écouteurs pour les notifications de métadonnées minutées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '67'
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

