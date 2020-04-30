---
description: TVSDK fournit des API et un exemple de code pour la gestion des périodes d’interruption de service.
seo-description: TVSDK fournit des API et un exemple de code pour la gestion des périodes d’interruption de service.
seo-title: Mise en oeuvre de la gestion des interruptions de service
title: Mise en oeuvre de la gestion des interruptions de service
uuid: db7f831c-5069-4426-bfe3-5fc51fec7930
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mise en oeuvre de la gestion des interruptions de service{#implement-blackout-handling}

TVSDK fournit des API et un exemple de code pour la gestion des périodes d’interruption de service.

Pour mettre en oeuvre la gestion des interruptions de service, notamment en fournissant du contenu alternatif pendant la coupure de service :

1. Configurez votre application pour détecter les balises d’arrêt dans un manifeste de flux en direct.

   ```java
   public void createMediaPlayer { 
       ... 
       String[] blackoutTags = {BLACKOUTTAG}; 
       PSDKConfig.setSubscribedTags(blackoutTags); 
       // For example: PTSDKConfig.setSubscribedTags({"#EXT-OATCLS-SCTE35"}); 
   }
   ```

1. Créez des écouteurs de événement pour les événements de métadonnées minutés dans les flux de premier plan et d’arrière-plan.

   ```java
   private MediaPlayer createMediaPlayer() { 
       mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, _playbackEventListener); 
       mediaPlayer.addEventListener(MediaPlayer.Event.BLACKOUTS, _blackoutsEventListener); 
   }
   ```

1. Mettez en oeuvre des gestionnaires de événement de métadonnées chronométrés pour les flux de premier plan et d’arrière-plan.

   Premier plan :

   ```java
   private final MediaPlayer.PlaybackEventListener _playbackEventListener =  
             new MediaPlayer.PlaybackEventListener() { 
       ... 
   
       @override 
       public void onTimedMetadata(TimedMetadata timedMetadata) { 
           if (timedMetadata.getName().equal(BLACKOUTTAG) &&  
               !_timedMetadataList.contains(timedMetadata)) { 
                 _timedMetadataList.add(timedMetadata); 
           } 
       } 
       ... 
   } 
   
   private final MediaPlayer.BlackoutsEventListener _blackoutsEventListener =  
     new MediaPlayer.BlackoutsEventListener() { 
       @Override 
       public void onTimedMetadataInBackgroundItem(TimedMetadata timedMetadata) { 
           TimedMetadata.Type type = timedMetadata.getType(); 
           if (type.equals(TimedMetadata.Type.TAG) && _mediaPlayer.getPlaybackRange() != null  
               && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
               if (!_timedMetadataList.contains(timedMetadata) && isBlackoutMetadata(timedMetadata)) { 
                   _timedMetadataList.add(timedMetadata); 
               } 
           } 
       } 
   
       @Override 
       public void onBackgroundManifestFailed() { 
           ... 
       } 
   }; 
   ```

1. Gérez `TimedMetadata` les objets lorsque `MediaPlayer` le temps s’exécute.

   ```java
   _playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           getActivity().runOnUiThread(new Runnable() { 
               @Override 
               public void run() { 
                   /* handle timedmetadata object list  */ 
                   if (_mediaPlayer != null && _timedMetadataList != null  
                       && _timedMetadataList.size() > 0) { 
                       if (_lastKnownStatus == MediaPlayer.PlayerState.PLAYING) { 
                           long localTime = _mediaPlayer.getLocalTime(); 
                           handleTimedMetadataList(localTime);      
                       } 
                   } 
               }                        
           }); 
       } 
   };
   ```

1. Créez des méthodes pour changer de contenu le début et la fin de la période d’interruption.

   ```java
   private void handleTimedMetadataList(long currentTime) { 
       for (int i = 0; i < _timedMetadataList.size(); i++) { 
           TimedMetadata timedMetadata = _timedMetadataList.get(i); 
           long diff = localTime - timedMetadata.getTime(); 
           if (!_timedMetadataDispatchedList.contains(timedMetadata) 
               && diff >= 0 
               && diff <= PLAYBACK_CLOCK_INTERVAL 
               && _mediaPlayer.shouldTriggerSubscribedTagEvent()) { 
                   // switch to blackout content 
               if (!_inBlackout && isBlackoutStartTimedMetadata(timedMetadata)) { 
                   MediaResource blackoutMediaResource = createBlackoutMediaResource(timedMetadata); 
   
                   //1. register current item as background item 
                   _mediaPlayer.registerCurrentItemAsBackgroundItem(); 
   
                   //2. replace current item with blackout item 
                   _mediaPlayer.replaceCurrentItem(blackoutMediaResource); 
   
                   //3. update qos metrics 
                   _mediaQosProvider.updateMetrics(_mediaPlayer); 
   
                   //4. maintain state 
                   _inBlackout = true; 
                   resetTimedMetada(); 
   
                   break; 
               } 
               // switch back to main content 
               else if (_inBlackout && isBlackoutEndTimedMetadata(timedMetadata)) { 
                   //1. register current item as background item 
                   _mediaPlayer.unregisterCurrentBackgroundItem(); 
   
                   //2. replace current item with blackout item 
                   _mediaPlayer.replaceCurrentItem(_oldMediaResource); 
   
                   //3. update qos metrics 
                   _mediaQosProvider.updateMetrics(_mediaPlayer); 
   
                   //4. maintain state 
                   _inBlackout = false; 
                   resetTimedMetada(); 
   
                   break; 
               } 
           } 
       } 
   }
   ```

1. Mettez à jour les plages impossibles à rechercher si la plage d’interruption se trouve dans le DVR du flux de lecture.

   ```java
   // prepare and update blackout nonSeekable ranges 
   
   List<TimeRange> blackoutRanges = prepareBlackoutRanges(_timedMetadataList); 
   if (blackoutRanges != null && blackoutRanges.size() > 0) { 
       int size = blackoutRanges.size(); 
       TimeRange[] blackoutRangesArray = blackoutRanges.toArray(new TimeRange[size]); 
       BlackoutMetadata blackoutMetadata = new BlackoutMetadata(blackoutRangesArray); 
       updateBlackoutMetadata(blackoutMetadata); 
   } 
   
   // function to update blackout metadata 
   private void updateBlackoutMetadata(BlackoutMetadata blackoutMetadata) { 
       MediaPlayerItem currentItem = _mediaPlayer.getCurrentItem(); 
       if (currentItem != null) { 
           Metadata metadata = currentItem.getResource().getMetadata(); 
           if (metadata != null) { 
               MetadataNode metadataNode = ((MetadataNode) metadata); 
               metadataNode.setNode(DefaultMetadataKeys.BLACKOUT_METADATA_KEY.getValue(),  
                                    blackoutMetadata); 
   
               for (int i = 0; i < blackoutMetadata.getNonSeekableRanges().length; i++) { 
                   TimeRange timeRange = blackoutMetadata.getNonSeekableRanges()[i]; 
               } 
           } 
       } 
   }
   ```

   >[!NOTE]
   >
   >Actuellement, pour plusieurs flux dynamiques à débit binaire, les profils de débit binaire (ABR) ajustables peuvent parfois être désynchronisés. Ceci provoque l’affichage d’objets de duplicata `timedMetadata` pour la même balise d’abonnement. Pour éviter des calculs incorrects non recherchables, il est vivement recommandé de vérifier si des plages non recherchables se chevauchent après vos calculs, comme dans l’exemple suivant :

   ```java
   List<TimeRange> rangesToRemove = new ArrayList<TimeRange>(); 
   
   for (int i = 0; i < nonSeekableRanges.size() - 1; i++) { 
       TimeRange range1 = nonSeekableRanges.get(i); 
       TimeRange range2 = nonSeekableRanges.get(i + 1); 
       if (range1.contains(range2.getBegin()) && !rangesToRemove.contains(range2)) { 
          rangesToRemove.add(range2); 
       } else if (range2.contains(range1.getBegin()) && !rangesToRemove.contains(range1)) { 
          rangesToRemove.add(range1); 
      } 
   } 
   
   if (nonSeekableRanges.size() > 0 && rangesToRemove.size() > 0) { 
       nonSeekableRanges.removeAll(rangesToRemove); 
       for (int i = 0; i < rangesToRemove.size(); i++) { 
           TimeRange range = rangesToRemove.get(i); 
       } 
   } 
   
   if (nonSeekableRanges.size() > 0 && rangesToRemove.size() > 0) { 
       nonSeekableRanges.removeAll(rangesToRemove); 
   }
   ```

