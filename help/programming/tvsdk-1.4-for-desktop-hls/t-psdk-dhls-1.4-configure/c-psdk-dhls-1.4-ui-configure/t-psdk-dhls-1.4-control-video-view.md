---
description: Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.
seo-description: Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.
seo-title: Contrôle de la position et de la taille de la vue vidéo
title: Contrôle de la position et de la taille de la vue vidéo
uuid: 2231c574-03cd-45a8-ab00-4a42f8e044f0
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Contrôler la position et la taille de la vue vidéo{#control-the-position-and-size-of-the-video-view}

Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.

TVSDK tente par défaut de conserver les proportions de la vue vidéo chaque fois que la taille ou la position de la vidéo change (en raison d’un changement apporté par l’application, par un commutateur de profil, ou par un commutateur de contenu, etc.).

Vous pouvez remplacer le comportement par défaut des proportions en spécifiant une autre *stratégie d’échelle*. Spécifiez la stratégie d&#39;échelle à l&#39;aide de la propriété `scalePolicy` de l&#39;objet `MediaPlayerView`. La stratégie d&#39;échelle par défaut de `MediaPlayerView` est définie avec une instance de la classe `MaintainAspectRatioScalePolicy`. Pour réinitialiser la stratégie d&#39;échelle, remplacez l&#39;instance par défaut de `MaintainAspectRatioScalePolicy` sur `MediaPlayerView.scalePolicy` par votre propre stratégie. (Vous ne pouvez pas définir la propriété `scalePolicy` sur une valeur nulle.)

1. Implémentez l&#39;interface `MediaPlayerViewScalePolicy` pour créer votre propre stratégie d&#39;échelle.

   Le `MediaPlayerViewScalePolicy` comporte une méthode :

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK utilise un objet `StageVideo` pour l’affichage de la vidéo. Comme les objets `StageVideo` ne figurent pas sur la liste d’affichage, le paramètre `viewPort` contient les coordonnées absolues de la vidéo.
   >
   >
   >Par exemple :
   >
   >
   ```
   >public class CustomScalePolicy implements MediaPlayerViewScalePolicy { 
   >       /** 
   >         * Default constructor. 
   >         */ 
   >       public function CustomScalePolicy() { 
   >       } 
   > 
   >    
      public function adjust(viewPort:Rectangle,  
   >                                                     videoWidth:Number,  
   >                                                     videoHeight:Number):Rectangle { 
   >               return customAdjustment(); 
   >       } 
   > 
   >    
      public function customAdjustment():Rectangle { 
   >               /* Your custom adjustment here */ 
   >               [...] 
   >       } 
   >}
   >```

1. Affectez votre implémentation à la propriété `MediaPlayerView`.

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. Ajoutez votre vue à la propriété `view` du lecteur multimédia.

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**Par exemple : Mettez la vidéo à l’échelle pour remplir toute la vue vidéo, sans conserver les proportions :**

```
package com.adobe.mediacore.samples.utils { 
    import com.adobe.mediacore.view.MediaPlayerViewScalePolicy; 
    import flash.geom.Rectangle; 
 
    /** 
    * A very simple custom scale policy - the video will fill the entire 
    * allocated space. The aspect ratio will not be kept. 
    */ 
    public class CustomScalePolicy implements MediaPlayerViewScalePolicy { 
 
        /** 
        * Default constructor. 
        */ 
        public function CustomScalePolicy() { 
        } 
 
        public function adjust(viewPort:Rectangle, 
                               videoWidth:Number,  
                               videoHeight:Number):Rectangle { 
            return viewPort; 
        } 
    } 
} 
 
var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
view.scalePolicy = new CustomScalePolicy(); 
addChild(view); 
mediaPlayer.view = view;
```

