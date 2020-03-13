---
description: Vous pouvez activer ou désactiver la fonction Résolution des publicités irrégulières à l’aide du mécanisme de chargement des publicités irrégulières (la résolution des publicités irrégulières est désactivée par défaut).
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: Vous pouvez activer ou désactiver la fonction Résolution des publicités irrégulières à l’aide du mécanisme de chargement des publicités irrégulières (la résolution des publicités irrégulières est désactivée par défaut).
seo-title: Activer la résolution des publicités paresseuses
title: Activer la résolution des publicités paresseuses
uuid: 91884eea-a622-4f5d-b6a8-36bb0050ba1d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Activer la résolution des publicités paresseuses {#enable-lazy-ad-resolving}

Vous pouvez activer ou désactiver la fonction Résolution des publicités irrégulières à l’aide du mécanisme de chargement des publicités irrégulières (la résolution des publicités irrégulières est désactivée par défaut).

Vous pouvez activer ou désactiver la résolution de publicités diffuses en appelant [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) avec true ou false.

* Utilisez les méthodes Boolean *hasDelayAdLoading* et *setDelayAdLoading* dans AdvertisingMetadata pour contrôler le timing de la résolution de la publicité et le positionnement des publicités dans le plan de montage chronologique :

   * Si *hasDelayAdLoading* renvoie false, TVSDK attend que toutes les publicités soient résolues et placées avant de passer à l’état PRÉPARÉ.
   * Si *hasDelayAdLoading* renvoie la valeur true, TVSDK résout uniquement les publicités initiales et les  à l’état PRÉPARÉ.

      * Les publicités restantes sont résolues et placées pendant la lecture.
   * Lorsque *hasPreroll *ou *hasLivePreroll* renvoie false, TVSDK suppose qu’il n’y a pas de publicité preroll et que la lecture du contenu  immédiatement. Ces valeurs sont définies par défaut sur true.


**API relatives à la résolution des publicités paresseuses :**

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

Pour représenter précisément les publicités comme des indices sur une barre de gommage, écoutez le `TimelineEvent`et retracez la barre de gommage chaque fois que vous recevez ce .

Lorsque l’option Résolution des publicités différées est activée pour les flux VOD, toutes les coupures publicitaires sont placées sur la chronologie. Cependant, la plupart des coupures publicitaires ne seront pas encore résolues. L’application peut déterminer s’il convient ou non de dessiner ces marqueurs en vérifiant la `TimelineMarker::getDuration()`. Si la valeur est supérieure à zéro, les publicités au sein de la coupure publicitaire ont été résolues.

TVSDK distribue ce lorsqu’une coupure publicitaire a été résolue, ainsi que lorsque le lecteur  l’état PRÉPARÉ.

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
