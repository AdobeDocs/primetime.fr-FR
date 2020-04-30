---
description: Vous pouvez activer ou désactiver la fonction Résolution des publicités en différé à l’aide du mécanisme de chargement des publicités en différé existant (la résolution des publicités en différé est activée par défaut).
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: Vous pouvez activer ou désactiver la fonction Résolution des publicités en différé à l’aide du mécanisme de chargement des publicités en différé existant (la résolution des publicités en différé est activée par défaut).
seo-title: Activer la résolution des annonces parentes
title: Activer la résolution des annonces parentes
uuid: a084ee0b-53af-4600-91f6-d30ccc89699d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Activer la résolution des annonces parentes {#enable-lazy-ad-resolving}

Vous pouvez activer ou désactiver la fonction Résolution des publicités en différé à l’aide du mécanisme de chargement des publicités en différé existant (la résolution des publicités en différé est activée par défaut).

Vous pouvez activer ou désactiver la résolution de publicités diffuses en appelant [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) avec `true` ou `false`.

1. Utilisez les `hasDelayAdLoading` méthodes et la valeur booléenne dans `setDelayAdLoading` `AdvertisingMetadata` pour contrôler le timing de la résolution de la publicité et le positionnement des publicités dans la chronologie :

   * Si `hasDelayAdLoading` renvoie false, TVSDK attend que toutes les publicités soient résolues et placées avant de passer à l’état PRÉPARÉ.
   * Si `hasDelayAdLoading` renvoie true, TVSDK résout uniquement les publicités et transitions initiales à l’état PRÉPARÉ. Les publicités restantes sont résolues et placées pendant la lecture.
   * Lorsque `hasPreroll` ou `hasLivePreroll` renvoient la valeur false, TVSDK suppose qu’il n’y a aucune publicité preroll et début la lecture du contenu immédiatement. Ces valeurs par défaut sont true.

      API relatives à la résolution des publicités parentes :

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

1. Pour représenter précisément les publicités comme des indices sur une barre de défilement, écoutez le `TimelineEvent` événement et redessinez la barre de défilement chaque fois que vous recevez ce événement.

   Lorsque l’option Résolution des publicités différées est activée pour les flux VOD, toutes les publicités ne sont pas placées sur la chronologie lorsque votre lecteur atteint l’état PRÉPARÉ. Par conséquent, votre lecteur doit redessiner explicitement la barre de défilement.

   TVSDK optimise l&#39;expédition de ce événement pour réduire au minimum le nombre de fois où vous devez redessiner la barre de défilement ; par conséquent, le nombre de événements de la chronologie n&#39;est pas lié au nombre de coupures publicitaires à placer sur la chronologie. Par exemple, si vous avez cinq coupures publicitaires, vous ne recevrez peut-être pas exactement cinq événements.

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

>Pour vérifier si la fonction Résolution des publicités différées est activée ou désactivée, appelez `AdvertisingMetadata.hasDelayAdLoading`. Une valeur renvoyée de `true` signifie que l’option Résolution des publicités différées est activée ; `false` signifie que la fonction est désactivée.

