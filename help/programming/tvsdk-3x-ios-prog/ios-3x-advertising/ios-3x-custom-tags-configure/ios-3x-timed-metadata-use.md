---
description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.
seo-description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.
seo-title: Utiliser des métadonnées minutées
title: Utiliser des métadonnées minutées
uuid: 1531780f-2502-4235-818c-6c0a6bf3d348
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Utiliser des métadonnées minutées {#use-timed-metadata}

Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.

Pour utiliser ces objets enregistrés `PTTimedMetadata` au cours de la lecture, utilisez le dictionnaire enregistré des objets de métadonnées temporisées [Stocker au fur et à mesure qu’ils sont distribués](../../../tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-custom-tags-configure/ios-3x-timed-metadata-store.md).

1. Extrayez et mettez à jour le temps de lecture actuel à partir de cette notification et recherchez tous les objets dont les débuts correspondent au temps de lecture actuel. `PTTimedMetadata`

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

1. Éliminez régulièrement `PTTimedMetadata` les instances obsolètes de la liste afin d’éviter que la mémoire ne continue à croître.