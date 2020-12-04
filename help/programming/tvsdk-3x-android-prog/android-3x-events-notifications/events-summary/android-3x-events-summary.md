---
description: Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.
seo-description: Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.
seo-title: Résumé des événements du lecteur Primetime
title: Résumé des événements du lecteur Primetime
uuid: b2ff74f2-c373-42da-a717-2f0550cbcb7f
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# Résumé des événements du lecteur Primetime {#primetime-player-events-summary}

Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.

## Événements {#events}

TVSDK vous avertit lorsque des événements auxquels votre application doit répondre se produisent. Chaque événement correspond à une classe d’écouteur, avec une méthode de rappel que vous devez implémenter.

>[!TIP]
>
>Les codes de événement sont les constantes de l&#39;énumération `MediaPlayerEvent`.

`AdBreakCompletedEventListener`

* **** SignificationLa lecture de la coupure publicitaire est terminée.

* **Rappel à implémenter** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Code événement** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **** SignificationUne coupure publicitaire a été ignorée pendant la lecture.

* **Rappel à implémenter** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Code événement** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **** SignificationLa lecture de la coupure publicitaire a commencé.

* **Rappel à implémenter** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Code événement** `AD_BREAK_START`

`AdClickedEventListener`

* **** SignificationUne publicité a fait l’objet d’un clic pendant la lecture.

* **Rappel à implémenter** `onAdClicked(AdClickEvent event)`
* **Code événement** `AD_CLICK`

`AdCompletedEventListener`

* **** SignificationLa lecture de la publicité est terminée.

* **Rappel à implémenter** `onAdCompleted(AdPlaybackEvent event)`

* **Code événement** `AD_COMPLETE`

`AdProgressEventListener`

* **** SignificationProgression de la création de rapports pendant la lecture.

* **Rappel à implémenter** `onAdProgress(AdPlaybackEvent event)`

* **Code événement** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **** SignificationPrimetime et la résolution des publicités est terminée. Ce événement ne s’applique qu’au contenu VOD.

* **Rappel à implémenter** `onAdResolutionComplete()`

* **Code événement** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **** SignificationLa lecture de la publicité a commencé.

* **Rappel à implémenter** `onAdStarted(AdPlaybackEvent event)`

* **Code événement** `AD_START`

`AudioUpdatedEventListener`

* **** SignificationUne nouvelle piste audio a été détectée.

* **Rappel à implémenter** `onAudioUpdated(MediaPlayerItemEvent event)`

* **Code événement** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **** SignificationLe lecteur a commencé à mettre en mémoire tampon.

* **Rappel à implémenter** `onBufferingBegin(BufferEvent event)`

* **Code événement** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **** SignificationLe lecteur a arrêté la mise en mémoire tampon.

* **Rappel à implémenter** `onBufferingEnd(BufferEvent event)`

* **Code événement** `BUFFERING_END`

`BufferPreparedEventListener&quot;

* **** SignificationLa mémoire tampon est préparée.

* **Rappel à implémenter** `onBufferPrepared()`

* **Code événement** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **** SignificationUne nouvelle piste de sous-titrage a été détectée.

* **Rappel à implémenter** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Code événement** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **** SignificationUne nouvelle métadonnées DRM a été détectée dans le flux média.

* **Rappel à implémenter** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Code événement** `DRM_METADATA`

`ItemCreatedEventListener`

* **** SignificationUn nouvel élément du lecteur multimédia a été créé.

* **Rappel à implémenter** `onItemCreated(MediaPlayerItemEvent event)`

* **Code événement** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **** SignificationDe nouvelles informations de chargement ont été créées pour l&#39;article en cours.

* **Rappel à implémenter** `onLoadComplete(MediaPlayerItemEvent event)`

* **Code événement** `ITEM_UPDATED`

`LoadInformationEventListener`

* **** SignificationUn nouveau segment a été chargé.

* **Rappel à implémenter** `onLoadInformation(LoadInformationEvent event)`

* **Code événement** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **** SignificationLe manifeste principal ou la liste de lecture a été mis à jour.

* **Rappel à implémenter** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Code événement** `MANIFEST_UPDATED`

`NotificationEventListener`

* **** SignificationL&#39;opération a échoué.

* **Rappel à implémenter** `onNotification(NotificationEvent event)`

* **Code événement** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **** SignificationLa plage de lecture a été mise à jour.

* **Rappel à implémenter** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Code événement** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **** SignificationUn nouveau taux de lecture est visible à l’écran.

* **Rappel à implémenter** `onRatePlaying(PlaybackRateEvent event)`

* **Code événement** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **** SignificationL&#39;attribut de taux de MediaPlayer a été défini.

* **Rappel à implémenter** `onRateSelected(PlaybackRateEvent event)`

* **Code événement** `RATE_SELECTED`

`PlayStartEventListener`

* **** SignificationLa lecture a commencé.

* **Rappel à implémenter** `onPlayStart()`

* **Code événement** `PLAY_START`

`ProfileChangeEventListener`

* **** SignificationLe profil actuel de MediaPlayer a changé.

* **Rappel à implémenter** `onProfileChanged(ProfileEvent event)`

* **Code événement** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **** SigniingPlayback a atteint une réservation de chronologie.

* **Rappel à implémenter** `onReservationReached(ReservationEvent event)`

* **Code événement** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **L&#39;opération** SigniingSeek a démarré.

* **Rappel à implémenter** `onSeekBegin(SeekEvent event)`

* **Code événement** `SEEK_BEGIN`

`SeekEndEventListener`

* **** SignificationL&#39;opération de recherche est terminée.

* **Rappel à implémenter** `onSeekEnd(SeekEvent event)`

* **Code événement** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **** SignificationLa position de recherche a été ajustée en raison de règles de lecture internes ou de règles métier externes.

* **Rappel à implémenter** `onPositionAdjusted(SeekEvent event)`

* **Code événement** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **** SignificationLa taille du média est disponible.

* **Rappel à implémenter** `onSizeAvailable(SizeAvailableEvent event)`

* **Code événement** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **** SignificationL’état de MediaPlayer a changé.

* **Rappel à implémenter** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Code événement** `STATUS_CHANGED`

`TimeChangeEventListener`

* **** SignificationLe curseur de lecture a changé.

* **Rappel à implémenter** `onTimeChanged(TimeChangeEvent event)`

* **Code événement** `TIME_CHANGED`

`TimedEventEventListener`

* **** SignificationL&#39;opération est terminée avec le temps nécessaire pour l&#39;opération.

* **Rappel à implémenter** `onTimedEvent(TimedEventEvent event)`

* **Code événement** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **** SignificationDe nouvelles métadonnées minutées ont été ajoutées à un élément en arrière-plan.

* **Rappel à implémenter** `onTimedMetadata(TimedMetadataEvent event)`

* **Code événement** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **** SignificationUne nouvelle métadonnée minutée a été détectée dans le flux média.

* **Rappel à implémenter** `onTimedMetadata(TimedMetadataEvent event)`

* **Code événement** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **** SignificationLa chronologie a été modifiée. Il est possible que des publicités aient été ajoutées ou supprimées de la chronologie.

* **Rappel à implémenter** `onTimelineUpdated(TimelineEvent event)`

* **Code événement** `TIMELINE_UPDATED`