---
description: TVSDK prend en charge l’affichage de publicités VPAID (Lecteur vidéo-Définition de l’interface publicitaire) linéaires dans une coupure publicitaire. La version 1.0 de VPAID nécessite un Flash, tandis que la version 2.0 fonctionne également avec le navigateur TVSDK et JavaScript.
title: Affichage de publicités VPAID linéaires dans une coupure publicitaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Affichage de publicités VPAID linéaires dans une coupure publicitaire{#display-linear-vpaid-ads-in-an-ad-break}

TVSDK prend en charge l’affichage de publicités VPAID (Lecteur vidéo-Définition de l’interface publicitaire) linéaires dans une coupure publicitaire. La version 1.0 de VPAID nécessite un Flash, tandis que la version 2.0 fonctionne également avec le navigateur TVSDK et JavaScript.

Pour afficher correctement les publicités VPAID, vous devez fournir un conteneur d’annonces ( `AdContainerView`) dans la variable `MediaPlayerContext` instance.

Limites pour les annonces VPAID :

* Les publicités VPAID n’ont pas nécessairement une durée prédéfinie, étant donné que la publicité peut être interactive. Par conséquent, la durée de la publicité (définie par la réponse du serveur de publicités) peut ne pas toujours correspondre exactement à la durée réelle de la publicité.
* Pour les annonces VPAID 1.0, TVSDK nécessite l’installation du lecteur Flash 14.0.0.160 ou version ultérieure sur l’appareil. Pour les versions antérieures du lecteur Flash, cette fonctionnalité est désactivée et les publicités VPAID 1.0 sont ignorées.

Pour configurer un conteneur d’annonces pour l’affichage de publicités VPAID (version 1.0 ou 2.0) dans une coupure publicitaire :

1. Utilisez l’exemple de code suivant pour configurer un conteneur publicitaire pouvant afficher des publicités VPAID.

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

1. Lorsque la vue est redimensionnée, réinitialisez la taille sur le conteneur d’annonces.

   ```
   adContainer.setSize(stage.stageWidth, stage.stageHeight);
   ```

   >[!NOTE]
   >
   >Lorsque vous obtenez un événement de changement en plein écran et que vous définissez la nouvelle taille sur le conteneur d’annonces, transmettez l’état d’affichage intermédiaire comme suit pour vous assurer que le lecteur redimensionne correctement :
   >
   >```
   >private function onFullScreenChange(event:FullScreenEvent):void { 
   >if (_adContainer) 
   >{ _adContainer.setSize(stage.stageWidth, stage.stageHeight, stage.displayState); } 
   >}
   >```
   >
