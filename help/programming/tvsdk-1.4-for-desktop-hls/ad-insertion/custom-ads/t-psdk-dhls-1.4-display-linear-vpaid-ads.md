---
description: TVSDK prend en charge l’affichage de publicités linéaires VPAID (Video Player-Ad Interface Definition) lors d’une coupure publicitaire. VPAID version 1.0 requiert Flash, tandis que la version 2.0 fonctionne également avec le navigateur TVSDK et JavaScript.
seo-description: TVSDK prend en charge l’affichage de publicités linéaires VPAID (Video Player-Ad Interface Definition) lors d’une coupure publicitaire. VPAID version 1.0 requiert Flash, tandis que la version 2.0 fonctionne également avec le navigateur TVSDK et JavaScript.
seo-title: Afficher des publicités VPAID linéaires dans une coupure publicitaire
title: Afficher des publicités VPAID linéaires dans une coupure publicitaire
uuid: 1f3a5426-79f5-49a1-a913-923708c09ade
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Afficher des publicités VPAID linéaires dans une coupure publicitaire{#display-linear-vpaid-ads-in-an-ad-break}

TVSDK prend en charge l’affichage de publicités linéaires VPAID (Video Player-Ad Interface Definition) lors d’une coupure publicitaire. VPAID version 1.0 requiert Flash, tandis que la version 2.0 fonctionne également avec le navigateur TVSDK et JavaScript.

Pour afficher correctement les publicités VPAID, vous devez fournir un publicitaire ( `AdContainerView`) au sein de l’ `MediaPlayerContext` instance.

Limites des publicités VPAID :

* Les publicités VPAID n’ont pas nécessairement une durée prédéfinie, étant donné qu’elles peuvent être interactives. Par conséquent, la durée de la publicité (définie par la réponse du serveur d’annonces) peut ne pas toujours correspondre exactement à la durée réelle de la publicité.
* Pour les annonces VPAID 1.0, TVSDK nécessite l’installation du lecteur Flash 14.0.0.160 ou version ultérieure sur le périphérique. Pour les versions antérieures du lecteur Flash, cette fonctionnalité est désactivée et les publicités VPAID 1.0 sont ignorées.

Pour configurer un publicitaire pour l&#39;affichage des publicités VPAID (version 1.0 ou 2.0) au sein d&#39;une coupure publicitaire :

1. Utilisez l’exemple de code suivant pour configurer un  publicitaire pouvant afficher des publicités VPAID.

   ```
   var context:MediaPlayerContext =  
     new MediaPlayerContext(_authorizedFeatureHelper.authorizedFeatures); 
   
   adContainer = new AdContainerView(); 
   adContainer.x = adContainer.y = 0; 
   adContainer.setSize(videoContainer.width, videoContainer.height); 
   addChild(adContainer); 
   
   context.adContainer = adContainer; 
   _player = new DefaultMediaPlayer(context);
   ```

1. Lorsque le est redimensionné, réinitialisez la taille sur l’ de la publicité.

   ```
   adContainer.setSize(stage.stageWidth, stage.stageHeight);
   ```

   >[!NOTE]
   >
   >Lorsque vous obtenez un  de modification en plein écran et que vous définissez la nouvelle taille sur le publicitaire, transmettez l’état d’affichage de la scène comme suit pour vous assurer que le lecteur se redimensionne correctement :    >
   >
   >
   ```>
   >private function onFullScreenChange(event:FullScreenEvent):void { 
   >if (_adContainer) 
   >{ _adContainer.setSize(stage.stageWidth, stage.stageHeight, stage.displayState); } 
   >}
   >```   >
   >



