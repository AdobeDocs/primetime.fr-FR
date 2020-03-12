---
description: Vous pouvez activer ou désactiver la fonction Résolution des publicités irrégulières à l’aide du mécanisme de chargement des publicités irrégulières existant (la résolution des publicités irrégulières est activée par défaut).
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: Vous pouvez activer ou désactiver la fonction Résolution des publicités irrégulières à l’aide du mécanisme de chargement des publicités irrégulières existant (la résolution des publicités irrégulières est activée par défaut).
seo-title: Activer la résolution des publicités paresseuses
title: Activer la résolution des publicités paresseuses
uuid: a084ee0b-53af-4600-91f6-d30ccc89699d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Activer la résolution des publicités paresseuses {#enable-lazy-ad-resolving}

Vous pouvez activer ou désactiver la fonction Résolution des publicités irrégulières à l’aide du mécanisme de chargement des publicités irrégulières existant (la résolution des publicités irrégulières est activée par défaut).

Vous pouvez activer ou désactiver la résolution de publicités diffuses en appelant [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) avec `true` ou `false`.

1. Utilisez les méthodes Boolean `hasDelayAdLoading` et `setDelayAdLoading` pour `AdvertisingMetadata` contrôler le timing de la résolution de la publicité et le positionnement des publicités dans la chronologie :

   * Si `hasDelayAdLoading` renvoie false, TVSDK attend que toutes les publicités soient résolues et placées avant de passer à l’état PRÉPARÉ.
   * Si la valeur `hasDelayAdLoading` est true, TVSDK résout uniquement les publicités initiales et les  à l’état PRÉPARÉ. Les publicités restantes sont résolues et placées pendant la lecture.
   * Lorsque `hasPreroll` ou `hasLivePreroll` renvoie false, TVSDK suppose qu’il n’existe aucune publicité preroll et la lecture immédiate du contenu. Ces valeurs par défaut sont true.

      API relatives à la résolution des publicités paresseuses :

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

1. Pour représenter précisément les publicités comme des indices sur une barre de gommage, écoutez le  du `TimelineEvent` et redessinez la barre de gommage chaque fois que vous recevez ce .

   Lorsque l’option Résolution des publicités différées est activée pour les flux VOD, toutes les publicités ne sont pas placées dans le plan de montage chronologique lorsque votre lecteur entre dans l’état PRÉPARÉ, de sorte que votre lecteur doit explicitement redessiner la barre de défilement.

   TVSDK optimise l’envoi de ce pour minimiser le nombre de fois où vous devez redessiner la barre de défilement ; par conséquent, le nombre de  de la chronologie n’est pas lié au nombre de coupures publicitaires à placer sur la chronologie. Par exemple, si vous avez cinq coupures publicitaires, vous ne recevrez peut-être pas exactement cinq .

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

