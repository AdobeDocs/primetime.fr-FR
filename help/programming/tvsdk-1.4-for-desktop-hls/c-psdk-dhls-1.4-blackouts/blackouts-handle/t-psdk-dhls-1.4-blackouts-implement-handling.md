---
description: TVSDK fournit des API et un exemple de code pour la gestion des périodes d’interruption.
seo-description: TVSDK fournit des API et un exemple de code pour la gestion des périodes d’interruption.
seo-title: Mise en oeuvre de la gestion du blocage
title: Mise en oeuvre de la gestion du blocage
uuid: 3b4e3f53-0e27-4369-85f2-940380ed16ac
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise en oeuvre de la gestion du blocage{#implement-blackout-handling}

TVSDK fournit des API et un exemple de code pour la gestion des périodes d’interruption.

Pour mettre en oeuvre la gestion des interruptions de service, y compris la fourniture de contenu alternatif pendant la coupure de service :

1. Configurez votre application pour détecter les balises d’arrêt dans un manifeste de flux en direct.

   ```
   private function startPlayback(resource:MediaResource):void { 
       ... 
       var tags:Vector.<String> = PSDKConfig.retrieveMediaPlayerItemConfig().subscribeTags; 
           tags.push(BlackoutHandler.BLACK_OUT_START_TAG); 
           tags.push(BlackoutHandler.BLACK_OUT_END_TAG); 
   
       PSDKConfig.retrieveMediaPlayerItemConfig().subscribeTags = tags; 
       ... 
   }
   ```

1. Créez des écouteurs de  pour les de métadonnées minutées  dans les flux de premier plan et d’arrière-plan.

   ```
   private function createMediaPlayer(context:MediaPlayerContext):void { 
       ... 
       _player.addEventListener(TimedMetadataEvent.TIMED_METADATA_AVAILABLE, onTimedMetadata); 
       _player.addEventListener(TimedMetadataEvent.TIMED_METADATA_IN_BACKGROUND_AVAILABLE,  
                                onTimedMetadataInBackground); 
       ... 
   }
   ```

1. Mettez en oeuvre des gestionnaires de  de métadonnées chronométrés pour les flux de premier plan et d’arrière-plan.

   Premier plan :

   ```
   private function onTimedMetadata(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       var start:uint = 0; 
       var end:uint = 0; 
       if (timedMetadata.type == TimedMetadataType.TAG) { 
           if (timedMetadata.name == BLACK_OUT_START_TAG) { 
               start = timedMetadata.time; 
               end = start + _player.playbackRange.end; // Get the duration 
               _blackoutRanges.push(new BlackoutMetadata(new TimeRange(start, end))); 
           } 
       } 
   }
   ```

   Contexte :

   ```
   private function onTimedMetadataInBackground(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       if (timedMetadata.type == TimedMetadataType.TAG) { 
           if (timedMetadata.name == BLACK_OUT_START_TAG) 
               _blackoutStartTime = timedMetadata.time; 
   
           if (timedMetadata.name == BLACK_OUT_END_TAG) { 
               _logger.debug("#onTimedMetadataInBackground New blackout end tag identified."); 
               _blackoutENDTime = timedMetadata.time; 
               var duration:int = ((_blackoutENDTime - _blackoutStartTime) - _offset) - _interval; 
               if (duration > 0) { 
                   _logger.debug("#onTimedMetadataInBackground Blackout {0} msec of blackout remaining  
                                 based on new/updated tags.", duration); 
                   _countdownTimer.reset(); 
                   _countdownTimer.delay = duration; 
                   _countdownTimer.start() 
               } 
           } 
       } 
   }
   ```

1. Préparez MediaPlayer pour les coupures de courant.

   ```
   public function prepareBlackoutRanges(timedMetadata:Vector.<TimedMetadata>):void { 
       _logger.debug('#prepareBlackoutRanges Calculating blackout ranges in DVR window'); 
       var start:uint = 0; 
       var end:uint = 0; 
       for (var i:uint = 0; i < timedMetadata.length; i++) { 
           if (timedMetadata[i].type == TimedMetadataType.TAG) { 
               if (timedMetadata[i].name == BLACK_OUT_END_TAG) { 
                   end = timedMetadata[i].time; 
                   if (start == 0) { 
                       _blackoutRanges.push(new TimeRange(0, end)); // Do we have any orphan end tags? 
                       end = 0; 
                   } 
                   else { 
                       _blackoutRanges.push(new TimeRange(start, end)); // If not... 
                       start = 0; 
                       end = 0; 
                   } 
               } 
               if (timedMetadata[i].name == BLACK_OUT_START_TAG) { 
                   start = timedMetadata[i].time; // Get the start time 
                   if (timedMetadata.length - 1 == i) 
                       _blackoutRanges.push(new TimeRange(start, _player.playbackRange.end)); 
               } 
           } 
       } 
   
       var blackoutRangeMetadata:BlackoutMetadata = new BlackoutMetadata(_blackoutRanges); 
       // Set the list of blackout ranges on the MediaPlayer 
       var metadata:Metadata = _player.currentItem.resource.metadata; 
       if(metadata) 
           metadata.setObject(DefaultMetadataKeys.BLACKOUT_METADATA_KEY, blackoutRangeMetadata); 
       _logger.debug("#prepareBlackoutRanges Printing DefaultMediaPlayer's representation of timedBlackoutMetadata."); 
   }
   ```

1. Configurez une vérification du de TimedMetadataObjects pour chaque occurrence d’une mise à jour de la position du curseur de lecture.

   ```
   private function onTimeChange(event:TimeChangeEvent):void { 
       if (!_inBlackout) { 
           for (var i:int = _blackoutRanges.length - 1; i >= 0; i--) { 
               if (containsTime(event.time) && !_seeking && !_inBlackout && !_adPlaying) { 
                   var index:int = getIndexForTime(event.time); 
                   if (_blackoutRanges[index].nonSeekableRange.end > _player.seekableRange.end) { 
                       _startTimer.reset(); 
                       _startTimer.start(); 
                       _offset = _player.currentTime - _blackoutRanges[index].nonSeekableRange.begin; 
                       var duration:int = _blackoutRanges[index].nonSeekableRange.duration -  
                                            (event.time - _blackoutRanges[index].nonSeekableRange.begin); 
                       _logger.debug("#onTimeChange Main content will resume in {0} msec.", duration); 
                       _blackoutStartTime = _blackoutRanges[index].nonSeekableRange.begin; 
                       initiate(); 
                       return; 
                   } else { 
                       _logger.debug("#onTimeChange Live blackout range start dectected."); 
                       _logger.debug("#onTimeChange Seekable range end {0}, Playable range {1},  
                                     Playhead {2}", _player.seekableRange.end,  
                                     _player.playbackRange.toString(), event.time); 
                       _player.seek(_blackoutRanges[index].nonSeekableRange.end); 
                       _seeking = true; 
                       return; 
                   } 
               } 
           } 
       } 
   }
   ```

1. Créez des méthodes pour changer de contenu au  et à la fin de la période d’arrêt.

   ```
   public function initiate(event:TimerEvent=null):void { 
       _inBlackout = true; 
       _logger.debug("#initiate Entering blackout"); 
       _player.removeEventListener(TimedMetadataEvent.TIMED_METADATA_AVAILABLE, onTimedMetadata); 
       _player.removeEventListener(TimeChangeEvent.TIME_CHANGED, onTimeChange); 
   
       // Register the current (original playback item) in background. 
       _player.registerCurrentItemAsBackgroundItem(); 
   
       // Replace the current playback item with the alternate stream. 
       _player.replaceCurrentResource(_alternate); 
   } 
   
   public function terminate(event:TimerEvent=null):void { 
       _inBlackout = false; 
       _offset = 0; 
       _logger.debug("#terminate Exiting blackout."); 
       _blackoutRanges.length = 0; 
       _blackoutRanges = new Vector.<BlackoutMetadata>(); 
       // Unregister background resource 
       _player.unregisterCurrentBackgroundItem(); 
       // Switch back to the original resource 
       _player.replaceCurrentResource(mainResource); 
       _player.addEventListener(TimedMetadataEvent.TIMED_METADATA_AVAILABLE, onTimedMetadata); 
       _player.addEventListener(TimeChangeEvent.TIME_CHANGED, onTimeChange); 
       _seekToBlackoutEnd = true; 
       // Reset countdown timer 
       if (_countdownTimer) { 
           _countdownTimer.reset(); 
           _startTimer.stop(); 
           _startTimer.reset(); 
           _interval = 0; 
       } 
   }
   ```

