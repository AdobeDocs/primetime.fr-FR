---
description: Pour recevoir des notifications concernant les balises dans le manifeste, enregistrez le ou les écouteurs de événement appropriés.
seo-description: Pour recevoir des notifications concernant les balises dans le manifeste, enregistrez le ou les écouteurs de événement appropriés.
seo-title: Ajouter écouteurs pour les notifications de métadonnées minutées
title: Ajouter écouteurs pour les notifications de métadonnées minutées
uuid: 419f4204-e3c3-4608-beb4-4cd259c8474d
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Ajouter écouteurs pour les notifications de métadonnées minutées{#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications concernant les balises dans le manifeste, enregistrez le ou les écouteurs de événement appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant les événements suivants, qui avertissent votre application de l’activité associée :

* `MediaPlayerItemEvent.ITEM_CREATED`: La liste initiale des `TimedMetadata` objets est disponible une fois `MediaPlayerItem` créée.

   Ce événement avertit votre application lorsque cela se produit.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Pour les flux en direct/linéaires où le manifeste/la liste de lecture est régulièrement actualisé, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/le manifeste mis à jour, de sorte que d’autres `TimedMetadata` objets peuvent être ajoutés à la `MediaPlayerItem.timedMetadata` propriété.

   Ce événement avertit votre application lorsque cela se produit.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Chaque fois qu’un nouvel `TimedMetadata` objet est créé, ce événement est distribué par MediaPlayer.

   Ce événement n’est pas distribué pour l’ `TimedMetadata` objet créé pendant la phase d’initialisation.

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

1. Enregistrez les écouteurs de événement.

   ```
   player.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
   player.addEventListener(TimedMetadataEvent.TIMED_METADATA_AVAILABLE,  
                           onTimedMetadataAvailable);
   ```

Les métadonnées ID3 sont distribuées par le biais de la même `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`méthode. Cela ne doit toutefois pas prêter à confusion, car vous pouvez utiliser la `type` propriété d’un objet TimedMetadata pour différencier TAG et ID3. Pour plus d’informations sur les balises ID3, voir Balises [](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md)ID3.