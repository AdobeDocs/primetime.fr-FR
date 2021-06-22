---
description: Votre application peut surveiller l’activité de votre lecteur et la modification de son état en écoutant les événements distribués par TVSDK.
title: Résumé des événements du lecteur Primetime
exl-id: 3912f140-1600-41fb-9dc4-306646b7cd85
source-git-commit: 59f7f8aa82be59c4012ee80648032600590bc4e1
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Résumé des événements du lecteur Primetime {#primetime-player-events-summary}

Votre application peut surveiller l’activité de votre lecteur et la modification de son état en écoutant les événements distribués par TVSDK.

## Événements {#events}

TVSDK vous avertit lorsque des événements, auxquels votre application doit répondre, se produisent. Chaque événement correspond à une classe listener, avec une méthode de rappel que vous devez implémenter.

>[!TIP]
>
>Les codes d’événement sont les constantes de l’énumération `MediaPlayerEvent`.

`AdBreakCompletedEventListener`

* **** Signification : la lecture de la coupure publicitaire est terminée.

* **Rappel à implémenter** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Code d’événement** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **** Signification : une coupure publicitaire a été ignorée pendant la lecture.

* **Rappel à implémenter** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Code d’événement** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **** Signification : la lecture de la coupure publicitaire a commencé.

* **Rappel à implémenter** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Code d’événement** `AD_BREAK_START`

`AdClickedEventListener`

* **** Signification : un utilisateur a cliqué sur une publicité pendant la lecture.

* **Rappel à implémenter** `onAdClicked(AdClickEvent event)`
* **Code d’événement** `AD_CLICK`

`AdCompletedEventListener`

* **** Signification : la lecture de la publicité est terminée.

* **Rappel à implémenter** `onAdCompleted(AdPlaybackEvent event)`

* **Code d’événement** `AD_COMPLETE`

`AdProgressEventListener`

* **** Signification de la progression des rapports lors de la lecture.

* **Rappel à implémenter** `onAdProgress(AdPlaybackEvent event)`

* **Code d’événement** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **** La résolution des publicités de Primetime est terminée. Cet événement s’applique uniquement au contenu VOD.

* **Rappel à implémenter** `onAdResolutionComplete()`

* **Code d’événement** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **** Signification : la lecture de la publicité a commencé.

* **Rappel à implémenter** `onAdStarted(AdPlaybackEvent event)`

* **Code d’événement** `AD_START`

`AudioUpdatedEventListener`

* **** Signification : une nouvelle piste audio a été détectée.

* **Rappel à implémenter** `onAudioUpdated(MediaPlayerItemEvent event)`

* **Code d’événement** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **** Signification : le lecteur a commencé la mise en mémoire tampon.

* **Rappel à implémenter** `onBufferingBegin(BufferEvent event)`

* **Code d’événement** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **** En d’autres termes, le lecteur a cessé la mise en mémoire tampon.

* **Rappel à implémenter** `onBufferingEnd(BufferEvent event)`

* **Code d’événement** `BUFFERING_END`

`BufferPreparedEventListener`

* **** En d’autres termes, la mémoire tampon est préparée.

* **Rappel à implémenter** `onBufferPrepared()`

* **Code d’événement** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **** Signification : un nouveau suivi de sous-titres a été détecté.

* **Rappel à implémenter** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Code d’événement** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **** Signification : de nouvelles métadonnées DRM ont été détectées dans le flux multimédia.

* **Rappel à implémenter** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Code d’événement** `DRM_METADATA`

`ItemCreatedEventListener`

* **** Signification : un nouvel élément du lecteur multimédia a été créé.

* **Rappel à implémenter** `onItemCreated(MediaPlayerItemEvent event)`

* **Code d’événement** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **** Signification : de nouvelles informations de chargement ont été créées pour l’élément actif.

* **Rappel à implémenter** `onLoadComplete(MediaPlayerItemEvent event)`

* **Code d’événement** `ITEM_UPDATED`

`LoadInformationEventListener`

* **** Signification : un nouveau segment a été chargé.

* **Rappel à implémenter** `onLoadInformation(LoadInformationEvent event)`

* **Code d’événement** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **** Signification : le manifeste principal ou la liste de lecture a été mis à jour.

* **Rappel à implémenter** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Code d’événement** `MANIFEST_UPDATED`

`NotificationEventListener`

* **** Signification : l’opération a échoué.

* **Rappel à implémenter** `onNotification(NotificationEvent event)`

* **Code d’événement** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **** Signification : la plage de lecture a été mise à jour.

* **Rappel à implémenter** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Code d’événement** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **** En d’autres termes, un nouveau taux de lecture est visible à l’écran.

* **Rappel à implémenter** `onRatePlaying(PlaybackRateEvent event)`

* **Code d’événement** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **** Signification : l’attribut rate de MediaPlayer a été défini.

* **Rappel à implémenter** `onRateSelected(PlaybackRateEvent event)`

* **Code d’événement** `RATE_SELECTED`

`PlayStartEventListener`

* **** Signification : la lecture a commencé.

* **Rappel à implémenter** `onPlayStart()`

* **Code d’événement** `PLAY_START`

`ProfileChangeEventListener`

* **** Signification : le profil actuel de MediaPlayer a changé.

* **Rappel à implémenter** `onProfileChanged(ProfileEvent event)`

* **Code d’événement** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **** Signification de la lecture a atteint une réservation de chronologie.

* **Rappel à implémenter** `onReservationReached(ReservationEvent event)`

* **Code d’événement** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **** L’opération SigniingSeek a démarré.

* **Rappel à implémenter** `onSeekBegin(SeekEvent event)`

* **Code d’événement** `SEEK_BEGIN`

`SeekEndEventListener`

* **** Signification : l’opération de recherche est terminée.

* **Rappel à implémenter** `onSeekEnd(SeekEvent event)`

* **Code d’événement** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **** Signification : la position de la recherche a été ajustée en raison de règles de lecture internes ou de règles commerciales externes.

* **Rappel à implémenter** `onPositionAdjusted(SeekEvent event)`

* **Code d’événement** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **** Signification : la taille du média est disponible.

* **Rappel à implémenter** `onSizeAvailable(SizeAvailableEvent event)`

* **Code d’événement** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **** Signification : l’état MediaPlayer a changé.

* **Rappel à implémenter** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Code d’événement** `STATUS_CHANGED`

`TimeChangeEventListener`

* **** Signification : le curseur de lecture a changé.

* **Rappel à implémenter** `onTimeChanged(TimeChangeEvent event)`

* **Code d’événement** `TIME_CHANGED`

`TimedEventEventListener`

* **** Signification : l’opération est terminée avec le temps nécessaire à l’opération.

* **Rappel à implémenter** `onTimedEvent(TimedEventEvent event)`

* **Code d’événement** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **** Signification : de nouvelles métadonnées minutées ont été ajoutées à un élément en arrière-plan.

* **Rappel à implémenter** `onTimedMetadata(TimedMetadataEvent event)`

* **Code d’événement** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **** Signification : de nouvelles métadonnées minutées ont été détectées dans le flux multimédia.

* **Rappel à implémenter** `onTimedMetadata(TimedMetadataEvent event)`

* **Code d’événement** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **** Signification : la chronologie a été modifiée. Il est possible que des publicités aient été ajoutées ou supprimées de la chronologie.

* **Rappel à implémenter** `onTimelineUpdated(TimelineEvent event)`

* **Code d’événement** `TIMELINE_UPDATED`
