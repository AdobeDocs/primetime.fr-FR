---
description: Votre application peut surveiller l’activité de votre lecteur et la modification de son état en écoutant les événements distribués par TVSDK.
title: Résumé des événements du lecteur Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# Résumé des événements du lecteur Primetime {#primetime-player-events-summary-overview}

Votre application peut surveiller l’activité de votre lecteur et la modification de son état en écoutant les événements distribués par TVSDK.

## Événements {#events}

TVSDK vous avertit lorsque des événements, auxquels votre application doit répondre, se produisent. Chaque événement correspond à une classe listener, avec une méthode de rappel que vous devez implémenter.

>[!TIP]
>
>Les codes d’événement sont les constantes de la variable `MediaPlayerEvent` enum.

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* ** Signification ** La lecture de la coupure publicitaire est terminée.

* ** Rappel pour implémenter ** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* ** Code d’événement ** `AD_BREAK_COMPLETE`

## AdBreakSkippedEventListener {#section_7AE5442442484F45B521D3309691C59C}

* ** Signification ** Une coupure publicitaire a été sautée pendant la lecture.

* ** Rappel pour implémenter ** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* ** Code d’événement ** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* ** Signification ** La lecture de la coupure publicitaire a commencé.

* ** Rappel pour implémenter ** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* ** Code d’événement ** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* ** Signification ** Un utilisateur a cliqué sur une publicité pendant la lecture.

* ** Rappel pour implémenter ** `onAdClicked(AdClickEvent event)`

* ** Code d’événement ** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* ** Signification ** La lecture de la publicité est terminée.

* ** Rappel pour implémenter ** `onAdCompleted(AdPlaybackEvent event)`

* ** Code d’événement ** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* ** Signification ** progression du reporting pendant la lecture.

* ** Rappel pour implémenter ** `onAdProgress(AdPlaybackEvent event)`

* ** Code d’événement ** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* ** Signification ** prise de décision et de résolution des publicités Primetime est terminée. Cet événement s’applique uniquement au contenu VOD.

* ** Rappel pour implémenter ** `onAdResolutionComplete()`

* ** Code d’événement ** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* ** Signification ** La lecture de la publicité a commencé.

* ** Rappel pour implémenter ** `onAdStarted(AdPlaybackEvent event)`

* ** Code d’événement ** `AD_START`

## AudioUpdatedEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* ** Signification ** Une nouvelle piste audio a été détectée.

* ** Rappel pour implémenter ** `onAudioUpdated(MediaPlayerItemEvent event)`

* ** Code d’événement ** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* ** Signification ** Le lecteur a commencé la mise en mémoire tampon.

* ** Rappel pour implémenter ** `onBufferingBegin(BufferEvent event)`

* ** Code d’événement ** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* ** Signification ** Le lecteur a cessé la mise en mémoire tampon.

* ** Rappel pour implémenter ** `onBufferingEnd(BufferEvent event)`

* ** Code d’événement ** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* ** Signification ** La mémoire tampon est préparée.

* ** Rappel pour implémenter ** `onBufferPrepared()`

* ** Code d’événement ** `BUFFER_PREPARED`

## CaptionsUpdatedEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* ** Signification ** Un nouveau suivi de sous-titres a été détecté.

* ** Rappel pour implémenter ** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* ** Code d’événement ** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* ** Signification ** Une nouvelle métadonnées DRM a été détectée dans le flux multimédia.

* ** Rappel pour implémenter ** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* ** Code d’événement ** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* ** Signification ** Un nouvel élément du lecteur multimédia a été créé.

* ** Rappel pour implémenter ** `onItemCreated(MediaPlayerItemEvent event)`

* ** Code d’événement ** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* ** Signification ** De nouvelles informations de chargement ont été créées pour l’élément actif.

* ** Rappel pour implémenter ** `onLoadComplete(MediaPlayerItemEvent event)`

* ** Code d’événement ** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* ** Signification ** Un nouveau segment a été chargé.

* ** Rappel pour implémenter ** `onLoadInformation(LoadInformationEvent event)`

* ** Code d’événement ** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdatedEventListener {#section_73709D121CED48C1B38550135DA55548}

* ** Signification ** Le manifeste principal ou la liste de lecture a été mis à jour.

* ** Rappel pour implémenter ** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* ** Code d’événement ** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* ** Signification ** L’opération a échoué.

* ** Rappel pour implémenter ** `onNotification(NotificationEvent event)`

* ** Code d’événement ** `OPERATION_FAILED`

## PlaybackRangeUpdatedEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* ** Signification ** La plage de lecture a été mise à jour.

* ** Rappel pour implémenter ** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* ** Code d’événement ** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayingEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* ** Signification ** Un nouveau taux de lecture est visible à l’écran.

* ** Rappel pour implémenter ** `onRatePlaying(PlaybackRateEvent event)`

* ** Code d’événement ** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* ** Signification ** L’attribut rate de MediaPlayer a été défini.

* ** Rappel pour implémenter ** `onRateSelected(PlaybackRateEvent event)`

* ** Code d’événement ** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* ** Signification ** La lecture a commencé.

* ** Rappel pour implémenter ** `onPlayStart()`

* ** Code d’événement ** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* ** Signification ** Le profil actuel de MediaPlayer a changé.

* ** Rappel pour implémenter ** `onProfileChanged(ProfileEvent event)`

* ** Code d’événement ** `PROFILE_CHANGED`

## ReserveReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* ** Signification ** la lecture a atteint une réservation de chronologie.

* ** Rappel pour implémenter ** `onReservationReached(ReservationEvent event)`

* ** Code d’événement ** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* ** Signification ** opération de recherche lancée.

* ** Rappel pour implémenter ** `onSeekBegin(SeekEvent event)`

* ** Code d’événement ** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* ** Signification ** L’opération de recherche est terminée.

* ** Rappel pour implémenter ** `onSeekEnd(SeekEvent event)`

* ** Code d’événement ** `SEEK_END`

## SeekPositionAdjustedEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* ** Signification ** La position de la recherche a été ajustée en raison de règles de lecture internes ou de règles commerciales externes.

* ** Rappel pour implémenter ** `onPositionAdjusted(SeekEvent event)`

* ** Code d’événement ** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* ** Signification ** La taille du média est disponible.

* ** Rappel pour implémenter ** `onSizeAvailable(SizeAvailableEvent event)`

* ** Code d’événement ** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* ** Signification ** L’état de MediaPlayer a changé.

* ** Rappel pour implémenter ** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* ** Code d’événement ** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* ** Signification ** Le curseur de lecture a changé.

* ** Rappel pour implémenter ** `onTimeChanged(TimeChangeEvent event)`

* ** Code d’événement ** `TIME_CHANGED`

## TimedEventEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* ** Signification ** L’opération est terminée avec le temps nécessaire pour l’opération.

* ** Rappel pour implémenter ** `onTimedEvent(TimedEventEvent event)`

* ** Code d’événement ** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* ** Signification ** De nouvelles métadonnées minutées ont été ajoutées à un élément en arrière-plan.

* ** Rappel pour implémenter ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Code d’événement ** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* ** Signification ** Une nouvelle métadonnée minutée a été détectée dans le flux multimédia.

* ** Rappel pour implémenter ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Code d’événement ** `TIMED_METADATA_AVAILABLE`

## TimelineUpdatedEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* ** Signification ** La chronologie a été modifiée. Il est possible que des publicités aient été ajoutées ou supprimées de la chronologie.

* ** Rappel pour implémenter ** `onTimelineUpdated(TimelineEvent event)`

* ** Code d’événement ** `TIMELINE_UPDATED`
