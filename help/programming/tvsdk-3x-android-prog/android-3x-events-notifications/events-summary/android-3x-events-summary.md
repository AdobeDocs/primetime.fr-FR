---
description: Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.
seo-description: Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.
seo-title: Résumé des événements du lecteur Primetime
title: Résumé des événements du lecteur Primetime
uuid: b2ff74f2-c373-42da-a717-2f0550cbcb7f
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Résumé des événements du lecteur Primetime {#primetime-player-events-summary}

Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.

## Événements {#events}

TVSDK vous avertit lorsque des événements auxquels votre application doit répondre se produisent. Chaque événement correspond à une classe d’écouteur, avec une méthode de rappel que vous devez implémenter.

>[!TIP]
>
>Les codes de événement sont les constantes de l&#39; `MediaPlayerEvent` enum.

`AdBreakCompletedEventListener`

* **Signification** La lecture de la coupure publicitaire est terminée.

* **Rappel à implémenter** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Code Événement** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **Signification** Une coupure publicitaire a été ignorée pendant la lecture.

* **Rappel à implémenter** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Code Événement** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **Signification** La lecture de la coupure publicitaire a commencé.

* **Rappel à implémenter** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Code Événement** `AD_BREAK_START`

`AdClickedEventListener`

* **Signification** Un utilisateur a cliqué sur une publicité pendant la lecture.

* **Rappel à implémenter** `onAdClicked(AdClickEvent event)`
* **Code Événement** `AD_CLICK`

`AdCompletedEventListener`

* **Signification** La lecture de la publicité est terminée.

* **Rappel à implémenter** `onAdCompleted(AdPlaybackEvent event)`

* **Code Événement** `AD_COMPLETE`

`AdProgressEventListener`

* **Cela signifie que** la progression du Rapports est en cours de lecture.

* **Rappel à implémenter** `onAdProgress(AdPlaybackEvent event)`

* **Code Événement** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **En d’autres termes** , Primetime et la résolution des publicités sont terminées. Ce événement ne s’applique qu’au contenu VOD.

* **Rappel à implémenter** `onAdResolutionComplete()`

* **Code Événement** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **Signification** La lecture de la publicité a commencé.

* **Rappel à implémenter** `onAdStarted(AdPlaybackEvent event)`

* **Code Événement** `AD_START`

`AudioUpdatedEventListener`

* **Signification** Une nouvelle piste audio a été détectée.

* **Rappel à implémenter** `onAudioUpdated(MediaPlayerItemEvent event)`

* **Code Événement** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **Signification** Le lecteur a commencé à mettre en mémoire tampon.

* **Rappel à implémenter** `onBufferingBegin(BufferEvent event)`

* **Code Événement** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **En d’autres termes** , le lecteur a arrêté la mise en mémoire tampon.

* **Rappel à implémenter** `onBufferingEnd(BufferEvent event)`

* **Code Événement** `BUFFERING_END`

`BufferPreparedEventListener&quot;

* **Signification** Le tampon est préparé.

* **Rappel à implémenter** `onBufferPrepared()`

* **Code Événement** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **Signification** Une nouvelle piste de sous-titrage a été détectée.

* **Rappel à implémenter** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Code Événement** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **Signification** Une nouvelle métadonnées DRM a été détectée dans le flux média.

* **Rappel à implémenter** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Code Événement** `DRM_METADATA`

`ItemCreatedEventListener`

* **Signification** Un nouvel élément du lecteur multimédia a été créé.

* **Rappel à implémenter** `onItemCreated(MediaPlayerItemEvent event)`

* **Code Événement** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **Signification** De nouvelles informations de chargement ont été créées pour l&#39;article en cours.

* **Rappel à implémenter** `onLoadComplete(MediaPlayerItemEvent event)`

* **Code Événement** `ITEM_UPDATED`

`LoadInformationEventListener`

* **Signification** Un nouveau segment a été chargé.

* **Rappel à implémenter** `onLoadInformation(LoadInformationEvent event)`

* **Code Événement** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **Signification** Le manifeste principal ou la liste de lecture a été mis à jour.

* **Rappel à implémenter** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Code Événement** `MANIFEST_UPDATED`

`NotificationEventListener`

* **Signification** Échec de l&#39;opération.

* **Rappel à implémenter** `onNotification(NotificationEvent event)`

* **Code Événement** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **Signification** La plage de lecture a été mise à jour.

* **Rappel à implémenter** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Code Événement** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **Signification** Un nouveau taux de lecture est visible à l’écran.

* **Rappel à implémenter** `onRatePlaying(PlaybackRateEvent event)`

* **Code Événement** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **Signification** L&#39;attribut de taux de MediaPlayer a été défini.

* **Rappel à implémenter** `onRateSelected(PlaybackRateEvent event)`

* **Code Événement** `RATE_SELECTED`

`PlayStartEventListener`

* **Signification** La lecture a commencé.

* **Rappel à implémenter** `onPlayStart()`

* **Code Événement** `PLAY_START`

`ProfileChangeEventListener`

* **Signification** Le profil actuel du lecteur multimédia a changé.

* **Rappel à implémenter** `onProfileChanged(ProfileEvent event)`

* **Code Événement** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **En d’autres termes** , la lecture a atteint une réservation de chronologie.

* **Rappel à implémenter** `onReservationReached(ReservationEvent event)`

* **Code Événement** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **En d’autres termes** , l’opération de recherche a démarré.

* **Rappel à implémenter** `onSeekBegin(SeekEvent event)`

* **Code Événement** `SEEK_BEGIN`

`SeekEndEventListener`

* **En d’autres termes** , l’opération de recherche est terminée.

* **Rappel à implémenter** `onSeekEnd(SeekEvent event)`

* **Code Événement** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **Signification** La position de recherche a été ajustée en raison de règles de lecture internes ou de règles métier externes.

* **Rappel à implémenter** `onPositionAdjusted(SeekEvent event)`

* **Code Événement** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **Signification** La taille du média est disponible.

* **Rappel à implémenter** `onSizeAvailable(SizeAvailableEvent event)`

* **Code Événement** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **Signification** de la modification de l’état de MediaPlayer.

* **Rappel à implémenter** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Code Événement** `STATUS_CHANGED`

`TimeChangeEventListener`

* **Signification** Le curseur de lecture a changé.

* **Rappel à implémenter** `onTimeChanged(TimeChangeEvent event)`

* **Code Événement** `TIME_CHANGED`

`TimedEventEventListener`

* **Signification** L’opération est terminée avec le temps nécessaire pour l’opération.

* **Rappel à implémenter** `onTimedEvent(TimedEventEvent event)`

* **Code Événement** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **Signification** Une nouvelle métadonnée minutée a été ajoutée à un élément en arrière-plan.

* **Rappel à implémenter** `onTimedMetadata(TimedMetadataEvent event)`

* **Code Événement** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **Signification** Une nouvelle métadonnée minutée a été détectée dans le flux média.

* **Rappel à implémenter** `onTimedMetadata(TimedMetadataEvent event)`

* **Code Événement** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **Signification** La chronologie a été modifiée. Il est possible que des publicités aient été ajoutées ou supprimées de la chronologie.

* **Rappel à implémenter** `onTimelineUpdated(TimelineEvent event)`

* **Code Événement** `TIMELINE_UPDATED`