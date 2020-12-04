---
description: Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.
seo-description: Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.
seo-title: Résumé des événements du lecteur Primetime
title: Résumé des événements du lecteur Primetime
uuid: ed3be4c2-8df3-4d96-a30b-74c196262798
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Résumé des événements du lecteur Primetime {#primetime-player-events-summary-overview}

Votre application peut surveiller l’activité de votre lecteur et l’état changeant du lecteur en écoutant les événements qui sont distribués par TVSDK.

## Événements {#events}

TVSDK vous avertit lorsque des événements auxquels votre application doit répondre se produisent. Chaque événement correspond à une classe d’écouteur, avec une méthode de rappel que vous devez implémenter.

>[!TIP]
>
>Les codes de événement sont les constantes de l&#39;énumération `MediaPlayerEvent`.

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* ** Signification ** La lecture de la coupure publicitaire est terminée.

* ** Rappel à implémenter ** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* ** Code de Événement ** `AD_BREAK_COMPLETE`

## AdBreakSkippedEventListener {#section_7AE5442442484F45B521D3309691C59C}

* ** Signification ** Une coupure publicitaire a été ignorée pendant la lecture.

* ** Rappel à implémenter ** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* ** Code de Événement ** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* ** Signification ** La lecture de la coupure publicitaire a commencé.

* ** Rappel à implémenter ** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* ** Code de Événement ** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* ** Signification ** Un utilisateur a cliqué sur une publicité pendant la lecture.

* ** Rappel à implémenter ** `onAdClicked(AdClickEvent event)`

* ** Code de Événement ** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* ** Signification ** La lecture de la publicité est terminée.

* ** Rappel à implémenter ** `onAdCompleted(AdPlaybackEvent event)`

* ** Code de Événement ** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* ** Signification ** Rapports de progression pendant la lecture.

* ** Rappel à implémenter ** `onAdProgress(AdPlaybackEvent event)`

* ** Code de Événement ** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* ** Signification ** Primetime et la résolution des publicités est terminée. Ce événement ne s’applique qu’au contenu VOD.

* ** Rappel à implémenter ** `onAdResolutionComplete()`

* ** Code de Événement ** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* ** Signification ** La lecture de la publicité a commencé.

* ** Rappel à implémenter ** `onAdStarted(AdPlaybackEvent event)`

* ** Code de Événement ** `AD_START`

## AudioUpdateEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* ** Signification ** Une nouvelle piste audio a été détectée.

* ** Rappel à implémenter ** `onAudioUpdated(MediaPlayerItemEvent event)`

* ** Code de Événement ** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* ** Signification ** Le lecteur a commencé la mise en mémoire tampon.

* ** Rappel à implémenter ** `onBufferingBegin(BufferEvent event)`

* ** Code de Événement ** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* ** Signification ** Le lecteur a arrêté la mise en mémoire tampon.

* ** Rappel à implémenter ** `onBufferingEnd(BufferEvent event)`

* ** Code de Événement ** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* ** Signification ** Le tampon est préparé.

* ** Rappel à implémenter ** `onBufferPrepared()`

* ** Code de Événement ** `BUFFER_PREPARED`

## CaptionsUpdateEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* ** Signification ** Une nouvelle piste de légende a été détectée.

* ** Rappel à implémenter ** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* ** Code de Événement ** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* ** Signification ** Une nouvelle métadonnées DRM a été détectée dans le flux média.

* ** Rappel à implémenter ** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* ** Code de Événement ** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* ** Signification ** Un nouvel élément du lecteur multimédia a été créé.

* ** Rappel à implémenter ** `onItemCreated(MediaPlayerItemEvent event)`

* ** Code de Événement ** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* ** Signification ** De nouvelles informations de chargement ont été créées pour l&#39;article en cours.

* ** Rappel à implémenter ** `onLoadComplete(MediaPlayerItemEvent event)`

* ** Code de Événement ** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* ** Signification ** Un nouveau segment a été chargé.

* ** Rappel à implémenter ** `onLoadInformation(LoadInformationEvent event)`

* ** Code de Événement ** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdateEventListener {#section_73709D121CED48C1B38550135DA55548}

* ** Signification ** Le manifeste principal ou la liste de lecture a été mis à jour.

* ** Rappel à implémenter ** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* ** Code de Événement ** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* ** Signification ** L&#39;opération a échoué.

* ** Rappel à implémenter ** `onNotification(NotificationEvent event)`

* ** Code de Événement ** `OPERATION_FAILED`

## PlaybackRangeUpdateEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* ** Signification ** La plage de lecture a été mise à jour.

* ** Rappel à implémenter ** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* ** Code de Événement ** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayingEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* ** Signification ** Un nouveau taux de lecture est visible à l’écran.

* ** Rappel à implémenter ** `onRatePlaying(PlaybackRateEvent event)`

* ** Code de Événement ** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* ** Signification ** L&#39;attribut de taux de MediaPlayer a été défini.

* ** Rappel à implémenter ** `onRateSelected(PlaybackRateEvent event)`

* ** Code de Événement ** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* ** Signification ** La lecture a commencé.

* ** Rappel à implémenter ** `onPlayStart()`

* ** Code de Événement ** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* ** Signification ** Le profil actuel de MediaPlayer a changé.

* ** Rappel à implémenter ** `onProfileChanged(ProfileEvent event)`

* ** Code de Événement ** `PROFILE_CHANGED`

## RéservationReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* ** Signification ** La lecture a atteint une réservation de chronologie.

* ** Rappel à implémenter ** `onReservationReached(ReservationEvent event)`

* ** Code de Événement ** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* ** Signification ** Opération de recherche commencée.

* ** Rappel à implémenter ** `onSeekBegin(SeekEvent event)`

* ** Code de Événement ** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* ** Signification ** L&#39;opération de recherche est terminée.

* ** Rappel à implémenter ** `onSeekEnd(SeekEvent event)`

* ** Code de Événement ** `SEEK_END`

## SeekPositionAdjustmentEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* ** Signification ** La position de recherche a été ajustée en raison de règles de lecture internes ou de règles de fonctionnement externes.

* ** Rappel à implémenter ** `onPositionAdjusted(SeekEvent event)`

* ** Code de Événement ** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* ** Signification ** La taille du média est disponible.

* ** Rappel à implémenter ** `onSizeAvailable(SizeAvailableEvent event)`

* ** Code de Événement ** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* ** Signification ** L’état de MediaPlayer a changé.

* ** Rappel à implémenter ** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* ** Code de Événement ** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* ** Signification ** Le curseur de lecture a changé.

* ** Rappel à implémenter ** `onTimeChanged(TimeChangeEvent event)`

* ** Code de Événement ** `TIME_CHANGED`

## TimedEventEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* ** Signification ** L&#39;opération est terminée avec le temps nécessaire pour l&#39;opération.

* ** Rappel à implémenter ** `onTimedEvent(TimedEventEvent event)`

* ** Code de Événement ** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* ** Signification ** Une nouvelle métadonnée minutée a été ajoutée à un élément en arrière-plan.

* ** Rappel à implémenter ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Code de Événement ** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* ** Signification ** Une nouvelle métadonnée minutée a été détectée dans le flux média.

* ** Rappel à implémenter ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Code de Événement ** `TIMED_METADATA_AVAILABLE`

## TimelineUpdateEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* ** Signification ** La chronologie a été modifiée. Il est possible que des publicités aient été ajoutées ou supprimées de la chronologie.

* ** Rappel à implémenter ** `onTimelineUpdated(TimelineEvent event)`

* ** Code de Événement ** `TIMELINE_UPDATED`