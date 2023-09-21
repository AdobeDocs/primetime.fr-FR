---
description: Vous pouvez activer une expérience de type télévision pour pouvoir rejoindre au milieu d’une publicité, dans des diffusions en direct.
title: Insertion partielle d’une coupure publicitaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Insertion partielle d’une coupure publicitaire {#partial-ad-break-insertion}

Vous pouvez activer une expérience de type télévision pour pouvoir rejoindre au milieu d’une publicité, dans des diffusions en direct.

La fonction coupure publicitaire partielle vous permet d’imiter une expérience de type TV où, si le client lance une diffusion en direct dans un milieu, elle démarre dans ce milieu. Cela revient à passer à une chaîne de télévision et les publicités s&#39;exécutent en toute transparence.

Par exemple, si un utilisateur se joint au milieu d’une coupure publicitaire de 90 secondes (trois publicités de 30 secondes), 10 secondes après la seconde publicité (c’est-à-dire à 40 secondes de la coupure publicitaire), ce qui suit se produit :

* La seconde publicité est lue pendant la durée restante (20 secondes) suivie de la troisième publicité.
* Les dispositifs de suivi publicitaires pour la publicité partiellement lue (la deuxième publicité) ne sont pas déclenchés. Seul le dispositif de suivi de la troisième publicité est déclenché.

Ce comportement n’est pas activé par défaut. Pour activer cette fonctionnalité dans votre application, procédez comme suit.

1. Désactivez les droits en direct, à l’aide de la méthode setEnableLivePreroll de la classe AdvertisingMetadata.

   ```
   advertisingMetadata.setEnableLivePreroll(String.valueOf(false))
   ```

1. Activez la préférence pour l’insertion de coupure publicitaire partielle. Utilisez la nouvelle méthode setPartialAdBreakPref dans l’interface MediaPlayer pour activer cette fonctionnalité. Utilisez la méthode getPartialAdBreakPref pour trouver l’état actuel de cette préférence.

   ```
   MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
   
          mediaPlayer.setPartialAdBreakPref(true); 
   ```

1. Cette fonctionnalité nécessite la mise en oeuvre d’un sélecteur de stratégie publicitaire personnalisé pour personnaliser le comportement. Si vous ne disposez pas déjà d’une implémentation personnalisée de la classe AdvertisingFactory, ajoutez une nouvelle implémentation AdvertisingFactory . Remplacez la méthode createAdPolicySelector . Cette méthode renvoie une nouvelle instance de l’implémentation d’AdPolicySelector.

   Vous trouverez ci-dessous un exemple de mise en oeuvre à titre de référence. L’exemple d’implémentation suivant est disponible à partir du package com.adobe.mediacore. Toutefois, il est simplifié pour une référence facile et il n’est pas recommandé d’utiliser en l’état.

   1. Sélecteur de stratégie d’annonce d’exemple

      ```
       package com.adobe.mediacore;
      
      import com.adobe.mediacore.logging.Log; 
      import com.adobe.mediacore.logging.Logger; 
      import com.adobe.mediacore.metadata.*; 
      import com.adobe.mediacore.timeline.advertising.*; 
      
      import java.util.ArrayList; 
      import java.util.List; 
      
      public class PartialAdBreakAdPolicySelector implements AdPolicySelector { 
          private static final String LOG_TAG = "[PSDK]::" + DefaultAdPolicySelector.class.getSimpleName(); 
          private final Logger _logger = Log.getLogger(LOG_TAG); 
      
          private final MediaPlayerItem _mediaPlayerItem; 
          private final AdBreakAsWatched _adBreakAsWatchedPolicy; 
      
          public PartialAdBreakAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
              _mediaPlayerItem = mediaPlayerItem; 
              _adBreakAsWatchedPolicy = extractAdBreakAsWatchedPolicy(_mediaPlayerItem); 
          } 
      
          @Override 
          public AdBreakPolicy selectPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectPolicyForAdBreak", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              if (adPolicyInfo.getAdBreakPlacements().size() > 0) { 
                  AdBreakPlacement adBreakTimelineItem = adPolicyInfo.getAdBreakPlacements().get(0); 
                  if (adPolicyInfo.getMode() == AdPolicyMode.SEEK && adBreakTimelineItem.getAdBreak().isWatched()) { 
                      return AdBreakPolicy.SKIP; 
                  } 
              } 
      
              AdSignalingMode adSignalingMode = AdSignalingMode.DEFAULT; 
              if (_mediaPlayerItem != null) { 
                  MetadataNode metadata = (MetadataNode) _mediaPlayerItem.getResource().getMetadata(); 
                  if (metadata != null) { 
                      AdvertisingMetadata advertisingMetadata = (AdvertisingMetadata) metadata.getNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue()); 
                      if (advertisingMetadata != null) { 
                          adSignalingMode = advertisingMetadata.getSignalingMode(); 
                      } 
                  } 
              } 
      
              // can't remove main content due to a ave bug, need to check if stream is live or ad signaling mode is manifest cue 
              if (_mediaPlayerItem.isLive() || adSignalingMode == AdSignalingMode.MANIFEST_CUES) { 
                  return AdBreakPolicy.PLAY; 
              } 
      
              return AdBreakPolicy.REMOVE_AFTER_PLAY; 
          } 
      
          @Override 
          public List<AdBreakPlacement> selectAdBreaksToPlay(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectAdBreaksToPlay", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              List<AdBreakPlacement> adBreakPlacements = adPolicyInfo.getAdBreakPlacements(); 
              if (adBreakPlacements != null) { 
                  int size = adBreakPlacements.size(); 
                  List<AdBreakPlacement> adBreaks = new ArrayList<AdBreakPlacement>(); 
                  if (size > 0 && adPolicyInfo.getCurrentTime() <= adPolicyInfo.getSeekToTime()) { 
                      AdBreakPlacement adBreak = adBreakPlacements.get(size - 1); 
                      if (!adBreak.getAdBreak().isWatched()) { 
                          adBreaks.add(adBreak); 
                          return adBreaks; 
                      } 
                  } 
              } 
      
              return null; 
          } 
      
          @Override 
          public AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectPolicyForSeekIntoAd", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              // If you really want to allow seek during ads (you likely do not). 
              return AdPolicy.PLAY; 
          } 
      
          @Override 
          public AdBreakAsWatched selectWatchedPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectWatchedPolicyForAdBreak", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              return _adBreakAsWatchedPolicy; 
          } 
      
          /** 
           * Extract the ad break watched policy for the specified media player item. 
           * 
           * @param item Associated media player item. 
           * @return a valid ad break watched policy. 
           */ 
          private AdBreakAsWatched extractAdBreakAsWatchedPolicy(MediaPlayerItem item) { 
              AdBreakAsWatched adBreakWatchedPolicy = AdBreakAsWatched.AD_BREAK_AS_WATCHED_ON_BEGIN; 
      
              if (item != null) { 
                  MetadataNode metadata = (MetadataNode) item.getResource().getMetadata(); 
                  if (metadata != null) { 
                      AdvertisingMetadata advertisingMetadata = (AdvertisingMetadata) metadata.getNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue()); 
                      if (advertisingMetadata != null) { 
                          adBreakWatchedPolicy = advertisingMetadata.getAdBreakAsWatched(); 
                      } 
                  } 
              } 
      
              return adBreakWatchedPolicy; 
          } 
      } 
      ```

   1. Exemple d’usine Advertising

      ```
      private AdvertisingFactory createPartialAdBreakFactory() { 
      return new AdvertisingFactory() { 
      @Override 
                   public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
                      return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
                   } 
      
      // Rest of the interface methods can be overridden as per your  
      // customization needs 
      // As shown next 
      @Override 
      public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
         return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
        } 
      // . . . 
      
       } 
      } 
      ```

   1. Enregistrement de AdvertisingFactory auprès du lecteur multimédia

      ```
      AdvertisingFactory advertisingFactory = createPartialAdBreakFactory();  
      
      if (advertisingFactory != null) { 
                  mediaPlayer.registerAdClientFactory(advertisingFactory); 
      } 
      ```

   1. Remplacement de la méthode createAdPolicySelector

      ```
      @Override 
      public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
         return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
      } 
      ```
