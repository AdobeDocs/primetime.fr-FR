---
description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.
seo-description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.
seo-title: Utiliser des métadonnées minutées
title: Utiliser des métadonnées minutées
uuid: 9bbdaefa-4ac5-4e08-92b4-15ebe5c46864
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---


# Utiliser des métadonnées minutées{#use-timed-metadata}

Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.

Pour utiliser ces objets `PTTimedMetadata` enregistrés au cours de la lecture, utilisez le dictionnaire enregistré de [Stocker les objets de métadonnées minutées au fur et à mesure de leur distribution](../../../tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-timed-metadata-store.md).

1. Extrayez et mettez à jour le temps de lecture actuel à partir de cette notification et recherchez tous les objets `PTTimedMetadata` dont les débuts correspondent au temps de lecture actuel.

   Vous pouvez utiliser ces objets pour effectuer diverses actions.

   Par exemple :

   ```
   - (void) onMediaPlayerTimeChange:(NSNotification *)notification 
   { 
       CMTimeRange seekableRange = self.player.seekableRange; 
       if (CMTIMERANGE_IS_VALID(seekableRange)) 
       { 
           int currentTime = (int) CMTimeGetSeconds(self.player.currentTime); 
           NSArray *allKeys = timedMetadataCollection ? [timedMetadataCollection allKeys] : [NSArray array]; 
           NSMutableArray *timedMetadatasToDelete = [[[NSMutableArray alloc] init] autorelease]; 
           int count = [allKeys count]; 
   
           for (int i=count - 1; i > -1; i--) 
           { 
              NSNumber *currTimedMetadataTime = allKeys[i]; 
              if ([currTimedMetadataTime integerValue] == currentTime) 
              { 
               /* 
                   Use the timed metadata here and remove it from the collection. 
               */ 
                NSLog (@"IN PLAYBACK TIME %i TO EXECUTE TIMEDMETADATA %@ scheduled at time %f",currentTime,currTimedMetadata.name,CMTimeGetSeconds(currTimedMetadata.time)); 
   
               PTTimedMetadata *currTimedMetadata = [timedMetadataCollection objectForKey:currTimedMetadataTime]; 
               [timedMetadatasToDelete addObject:currTimedMetadataTime]; 
              } 
           } 
   
           for (int i=0; i<[timedMetadatasToDelete count]; i++) 
           { 
               NSNumber *timedMetadataToDelete = timedMetadatasToDelete[i]; 
               [timedMetadataCollection removeObjectForKey:timedMetadataToDelete]; 
           } 
       } 
   }
   ```

1. Éliminez régulièrement les instances `PTTimedMetadata` obsolètes de la liste afin d’éviter que la mémoire ne continue à croître.
