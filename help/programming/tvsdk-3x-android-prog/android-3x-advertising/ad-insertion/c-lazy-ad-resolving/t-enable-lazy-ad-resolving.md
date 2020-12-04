---
description: Vous pouvez activer ou désactiver la fonction Résolution des publicités en différé à l’aide du mécanisme de chargement des publicités en différé existant (la résolution des publicités en différé est désactivée par défaut).
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: Vous pouvez activer ou désactiver la fonction Résolution des publicités en différé à l’aide du mécanisme de chargement des publicités en différé existant (la résolution des publicités en différé est désactivée par défaut).
seo-title: Activer la résolution des annonces parentes
title: Activer la résolution des annonces parentes
uuid: 91884eea-a622-4f5d-b6a8-36bb0050ba1d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# Activer la résolution des publicités parentes {#enable-lazy-ad-resolving}

Vous pouvez activer ou désactiver la fonction Résolution des publicités en différé à l’aide du mécanisme de chargement des publicités en différé existant (la résolution des publicités en différé est désactivée par défaut).

Vous pouvez activer ou désactiver la résolution de publicités diffuses en appelant [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) avec true ou false.

* Utilisez les méthodes booléennes *hasDelayAdLoading* et *setDelayAdLoading* dans AdvertisingMetadata pour contrôler le timing de la résolution de la publicité et le positionnement des publicités sur le plan de montage chronologique :

   * Si *hasDelayAdLoading* renvoie false, TVSDK attend que toutes les publicités soient résolues et placées avant de passer à l’état PRÉPARÉ.
   * Si *hasDelayAdLoading* renvoie true, TVSDK résout uniquement les publicités et les transitions initiales à l’état PRÉPARÉ.

      * Les publicités restantes sont résolues et placées pendant la lecture.
   * Lorsque *hasPreroll *ou *hasLivePreroll* renvoie false, TVSDK suppose qu’il n’y a aucune publicité preroll et début la lecture du contenu immédiatement. Il s’agit par défaut de la valeur true.


**API relatives à la résolution des publicités parentes :**

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

Pour représenter précisément les publicités comme des indices sur une barre de défilement, écoutez le `TimelineEvent`événement et retracez la barre de défilement chaque fois que vous recevez ce événement.

Lorsque l’option Résolution des publicités différées est activée pour les flux VOD, toutes les coupures publicitaires sont placées sur la chronologie, mais la plupart des coupures publicitaires ne seront pas encore résolues. L&#39;application peut déterminer si ces marqueurs doivent être dessinés ou non en vérifiant le `TimelineMarker::getDuration()`. Si la valeur est supérieure à zéro, les publicités au sein de la coupure publicitaire ont été résolues.

TVSDK distribue ce événement lorsqu’une coupure publicitaire a été résolue, ainsi que lorsque le lecteur transition à l’état PRÉPARÉ.

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
