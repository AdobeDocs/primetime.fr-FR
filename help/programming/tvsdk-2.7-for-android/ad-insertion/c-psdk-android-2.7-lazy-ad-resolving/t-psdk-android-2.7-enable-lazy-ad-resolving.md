---
description: Vous pouvez activer ou désactiver la fonction Résolution des publicités différées à l’aide du mécanisme de chargement de publicités différées existant (la résolution des publicités différées est activée par défaut).
keywords: Lazy;résolution de publicité;chargement de publicité;delayLoading
title: Activation de la résolution des publicités différées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Activation de la résolution des publicités différées {#enable-lazy-ad-resolving}

Vous pouvez activer ou désactiver la fonction Résolution des publicités différées à l’aide du mécanisme de chargement de publicités différées existant (la résolution des publicités différées est activée par défaut).

Vous pouvez activer ou désactiver la résolution des publicités différées en appelant [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) avec `true` ou `false`.

1. Utilisation du booléen `hasDelayAdLoading` et `setDelayAdLoading` méthodes dans `AdvertisingMetadata` pour contrôler le délai de résolution des publicités et le placement des publicités dans la chronologie :

   * If `hasDelayAdLoading` renvoie false, TVSDK attend que toutes les publicités soient résolues et placées avant de passer à l’état PRÉPARÉ.
   * If `hasDelayAdLoading` renvoie true, TVSDK résout uniquement les publicités initiales et les transitions à l’état PRÉPARÉ. Les publicités restantes sont résolues et placées pendant la lecture.
   * When `hasPreroll` ou `hasLivePreroll` return false, TVSDK suppose qu’il n’y a pas de publicité preroll et commence la lecture du contenu immédiatement. Par défaut, cette valeur est définie sur true.

     API relatives à la résolution de publicités différée :

     ```
     Class: 
        com.adobe.mediacore.metadata.AdvertisingMetadata 
     
     Methods: 
     […] 
         public final boolean hasDelayAdLoading() // Check if Lazy Ad Resolving enabled 
         public final void setDelayAdLoading()    // Enable or disable Lazy Ad Resolving 
         public final boolean hasPreroll()        // Check for existence of pre-roll ads 
         public final void setPreroll()           // Set pre-roll true or false 
         public final boolean hasLivePreroll()    // Check for live pre-roll ads 
         public final void setLivePreroll()       // Set live pre-roll true or false 
     […]
     ```

1. Pour représenter précisément les publicités comme repères sur une barre de défilement, écoutez le `TimelineEvent` et redessinez la barre de défilement chaque fois que vous recevez cet événement.

   Lorsque la résolution des publicités différées est activée pour les flux VOD, toutes les publicités ne sont pas placées sur la chronologie lorsque votre lecteur passe à l’état PRÉPARÉ. Votre lecteur doit donc redessiner explicitement la barre de défilement.

   TVSDK optimise la distribution de cet événement afin de minimiser le nombre de fois où vous devez redessiner la barre de défilement. Par conséquent, le nombre d’événements de la chronologie n’est pas lié au nombre de coupures publicitaires à placer sur la chronologie. Par exemple, si vous avez cinq coupures publicitaires, vous ne recevrez peut-être pas exactement cinq événements.

   ```java
   mediaPlayer.addEventListener 
       (MediaPlayerEvent.TIMELINE_UPDATED, timelineUpdatedEventListener); 
   /** 
    * ... 
    */ 
   public void onTimelineUpdated(TimelineEvent event) { 
   
       for (PlaybackManagerEventListener listener : eventListeners) { 
           listener.onUpdate(getLocalSeekRange(), event.getTimeline()); 
       } 
   } 
   ```

>Pour vérifier si la fonction Résolution des publicités différées est activée ou désactivée, appelez `AdvertisingMetadata.hasDelayAdLoading`. Une valeur renvoyée de `true` signifie que la résolution des publicités différée est activée ; `false` signifie que la fonction est désactivée.
