---
description: Pour recevoir des notifications sur des balises dans le manifeste, enregistrez le ou les écouteurs d’événement appropriés.
title: Ajout d’écouteurs pour les notifications de métadonnées minutées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Ajout d’écouteurs pour les notifications de métadonnées minutées{#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur des balises dans le manifeste, enregistrez le ou les écouteurs d’événement appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant les événements suivants, qui notifient votre application de l’activité associée :

* `MediaPlayerItemEvent.ITEM_CREATED`: la liste initiale de `TimedMetadata` est disponible après la `MediaPlayerItem` est créée.

  Cet événement avertit votre application lorsque cela se produit.

* `MediaPlayerItemEvent.ITEM_UPDATED`: pour les flux en direct/linéaires où la liste de lecture/manifeste s’actualise régulièrement, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/manifeste mise à jour, donc des balises supplémentaires `TimedMetadata` peut être ajouté à la variable `MediaPlayerItem.timedMetadata` .

  Cet événement avertit votre application lorsque cela se produit.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: chaque fois qu’une nouvelle `TimedMetadata` est créé, cet événement est distribué par MediaPlayer.

  Cet événement n’est pas distribué pour la variable `TimedMetadata` créé lors de la phase d’initialisation.

1. Mettez en oeuvre les écouteurs appropriés.

   ```
   private function onItemCreated(event:MediaPlayerItemEvent):void { 
       var timedMetadataCollection:Vector.<TimedMetadata> = event.item.timedMetadata; 
       // process the timed metadata collection 
   } 
   
   private function onItemUpdated(event:MediaPlayerItemEvent):void { 
       var timedMetadataCollection:Vector.<TimedMetadata> = event.item.timedMetadata; 
       // process the timed metadata collection 
   } 
   
   private function onTimedMetadataAvailable(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       // process timed metadata 
   }
   ```

1. Enregistrez les écouteurs d’événement.

   ```
   player.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
   player.addEventListener(TimedMetadataEvent.TIMED_METADATA_AVAILABLE,  
                           onTimedMetadataAvailable);
   ```

Les métadonnées ID3 sont distribuées via le même `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`. Cela ne doit toutefois pas prêter à confusion, car vous pouvez utiliser un objet TimedMetadata de `type` pour différencier TAG et ID3. Pour plus d’informations sur les balises ID3, voir [Balises ID3](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md).
