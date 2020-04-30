---
description: Par défaut, TVSDK force la lecture d’une coupure publicitaire lorsque l’utilisateur effectue une recherche sur une coupure publicitaire. Vous pouvez personnaliser le comportement pour ignorer une coupure publicitaire si le temps écoulé depuis la fin d’une coupure précédente se situe dans un certain nombre de minutes.
seo-description: Par défaut, TVSDK force la lecture d’une coupure publicitaire lorsque l’utilisateur effectue une recherche sur une coupure publicitaire. Vous pouvez personnaliser le comportement pour ignorer une coupure publicitaire si le temps écoulé depuis la fin d’une coupure précédente se situe dans un certain nombre de minutes.
seo-title: Ignorer les coupures publicitaires pour une période
title: Ignorer les coupures publicitaires pour une période
uuid: 1a18d5fd-c957-481b-83ae-2129590c1678
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ignorer les coupures publicitaires pour une période{#skip-ad-breaks-for-a-period-of-time}

Par défaut, TVSDK force la lecture d’une coupure publicitaire lorsque l’utilisateur effectue une recherche sur une coupure publicitaire. Vous pouvez personnaliser le comportement pour ignorer une coupure publicitaire si le temps écoulé depuis la fin d’une coupure précédente se situe dans un certain nombre de minutes.

>[!IMPORTANT]
>
>En cas de recherche interne pour ignorer une publicité, la lecture peut présenter une légère pause.

L’exemple suivant d’un sélecteur de stratégie d’annonce personnalisé ignore les publicités au cours des cinq prochaines minutes (heure du mur) après qu’un utilisateur ait assisté à une coupure publicitaire.

1. Etendez le sélecteur de stratégie d’annonce par défaut pour remplacer le comportement par défaut.

   ```
   /** 
    * Custom ad policy selector. 
    */ 
   public class CustomAdPolicySelector extends DefaultAdPolicySelector { 
   
       /** 
        * Default constructor. 
        * 
        * @param item Associated media player item. 
        */ 
       public function CustomAdPolicySelector(item:MediaPlayerItem) { 
           super(item); 
   
           item.player.addEventListener(AdBreakPlaybackEvent.AD_BREAK_COMPLETED,  
                                        onAdBreakCompleted); 
       } 
   
       override public function selectPolicyForAdBreak(adPolicyInfo:AdPolicyInfo):String { 
           if (shouldPlayAds()) { 
               return super.selectPolicyForAdBreak(adPolicyInfo); 
           } 
   
           return AdBreakPolicy.SKIP; 
       } 
   
       override public function selectAdBreaksToPlay(adPolicyInfo:AdPolicyInfo):Vector.<AdBreakTimelineItem> { 
           if (shouldPlayAds()) { 
               return super.selectAdBreaksToPlay(adPolicyInfo); 
           } 
   
           return new Vector.<AdBreakTimelineItem>(); 
       } 
   
       override public function selectPolicyForSeekIntoAd(adPolicyInfo:AdPolicyInfo):String { 
           if (shouldPlayAds()) { 
               return super.selectPolicyForSeekIntoAd(adPolicyInfo); 
           } 
   
           return AdPolicy.SKIP_TO_NEXT_AD_IN_AD_BREAK; 
       } 
   
       private function onAdBreakCompleted(event:AdBreakPlaybackEvent):void { 
           _lastAdBreakPlayedTime = new Date().valueOf(); 
       } 
   
       private function shouldPlayAds():Boolean { 
           var currentTime:Number = new Date().valueOf(); 
           return isNaN(_lastAdBreakPlayedTime) 
                   ||  (currentTime - _lastAdBreakPlayedTime > _minimumInterval); 
       } 
   
       private var _lastAdBreakPlayedTime:Number = NaN; 
       private var _minimumInterval:Number = 300000; // 5 minutes in milliseconds 
   }
   ```

1. Créez une fabrique de publicités qui utilise votre sélecteur personnalisé.

   ```
   public class CustomAdPolicyContentFactory extends DefaultContentFactory { 
   
       private var _adPolicySelector:CustomAdPolicySelector; 
   
       /** 
        * Default constructor. 
        */ 
       public function CustomAdPolicyContentFactory() { 
   
       } 
   
       /** 
       * @inheritDoc 
       */ 
       override protected function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
       if (!_adPolicySelector) { 
           _adPolicySelector = new CustomAdPolicySelector(item); 
       } 
   
       return _adPolicySelector; 
       } 
   }
   ```

1. Enregistrez la nouvelle classe d&#39;usine publicitaire à utiliser avec MediaPlayer.

   ```
   var mediaResource:MediaResource =  
     MediaResource.createFromUrl("https://example.org/stream.m3u8", null); 
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     PSDKConfig.retrieveMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomAdPolicyContentFactory(); 
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

