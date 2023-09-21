---
description: Vous pouvez activer ou désactiver la fonction Résolution des publicités différées à l’aide du mécanisme de chargement de publicités différées existant (la résolution des publicités différées est désactivée par défaut).
keywords: Lazy;résolution de publicité;chargement de publicité;delayLoading
title: Activation de la résolution des publicités différées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Activation de la résolution des publicités différées {#enable-lazy-ad-resolving}

Vous pouvez activer ou désactiver la fonction Résolution des publicités différées à l’aide du mécanisme de chargement de publicités différées existant (la résolution des publicités différées est désactivée par défaut).

Vous pouvez activer ou désactiver la résolution des publicités différées en appelant [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) avec true ou false.

* Utilisation du booléen *hasDelayAdLoading* et *setDelayAdLoading* méthodes dans AdvertisingMetadata pour contrôler le délai de résolution de la publicité et le placement des publicités sur la chronologie :

   * If *hasDelayAdLoading* renvoie false, TVSDK attend que toutes les publicités soient résolues et placées avant de passer à l’état PRÉPARÉ.
   * If *hasDelayAdLoading* renvoie true, TVSDK résout uniquement les publicités initiales et les transitions à l’état PRÉPARÉ.

      * Les publicités restantes sont résolues et placées pendant la lecture.

   * Lorsque *hasPreroll* ou *hasLivePreroll* return false, TVSDK suppose qu’il n’y a pas de publicité preroll et commence la lecture du contenu immédiatement. Par défaut, ils sont définis sur true.

**API relatives à la résolution de publicités différée :**

```
Class:    com.adobe.mediacore.metadata.AdvertisingMetadata 
Methods: 
    public final boolean hasDelayAdLoading() // Check if Lazy Ad Resolving enabled 
    public final void setDelayAdLoading() // Enable or disable Lazy Ad Resolving 
    public final void setDelayAdLoadingTolerance() // Sets the Lazy Ad Resolving Tolerance level.  This value is added to the BufferControlParameters::playBufferTime and the content's EXT-X-TARGETDURATION to determine when ad breaks should resolve 
    public final double getDelayAdLoadingTolerance() // Gets the Lazy Ad Resolving Tolerance level 
    public final boolean hasPreroll() // Check for existence of pre-roll ads 
    public final void setPreroll() // Set pre-roll true or false 
    public final boolean hasLivePreroll() // Check for live pre-roll ads 
    public final void setLivePreroll() // Set live pre-roll true or false

Class:     com.adobe.mediacore.timeline.TimelineMarker 
Methods: 
    public double getDuration() // Returns the current duration of the TimelineMarker.  This will be zero if the ad break has not yet resolved. 
    public Placement.Type getPlacementType() // Returns whether
```

Pour représenter précisément les publicités comme repères sur une barre de défilement, écoutez le `TimelineEvent`et redessinez la barre de défilement chaque fois que vous recevez cet événement.

Lorsque la résolution différée des publicités est activée pour les flux VOD, toutes les coupures publicitaires sont placées sur la chronologie. Toutefois, de nombreuses coupures publicitaires ne seront pas encore résolues. L’application peut déterminer si ces marqueurs doivent être dessinés ou non en vérifiant la variable `TimelineMarker::getDuration()`. Si la valeur est supérieure à zéro, les publicités dans la coupure publicitaire ont été résolues.

TVSDK distribue cet événement lorsqu’une coupure publicitaire a été résolue, ainsi que lorsque le lecteur passe à l’état PRÉPARÉ .

```
mediaPlayer.addEventListener(MediaPlayerEvent.TIMELINE_UPDATED, timelineUpdatedEventListener); 
/** 
* ... 
*/ 
public void onTimelineUpdated(TimelineEvent event) { 
for (PlaybackManagerEventListener listener : eventListeners) { 
  listener.onUpdate(getLocalSeekRange(), event.getTimeline()); 
}
```
