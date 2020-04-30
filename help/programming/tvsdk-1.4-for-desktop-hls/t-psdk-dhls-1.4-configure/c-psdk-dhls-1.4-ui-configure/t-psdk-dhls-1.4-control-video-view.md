---
description: Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.
seo-description: Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.
seo-title: Contrôle de la position et de la taille de la vue vidéo
title: Contrôle de la position et de la taille de la vue vidéo
uuid: 2231c574-03cd-45a8-ab00-4a42f8e044f0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Contrôle de la position et de la taille de la vue vidéo{#control-the-position-and-size-of-the-video-view}

Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.

TVSDK tente par défaut de conserver les proportions de la vue vidéo chaque fois que la taille ou la position de la vidéo change (en raison d’un changement apporté par l’application, par un commutateur de profil, ou par un commutateur de contenu, etc.).

Vous pouvez remplacer le comportement par défaut des proportions en spécifiant une autre stratégie *d’*&#x200B;échelle. Spécifiez la stratégie d&#39;échelle à l&#39;aide de la `MediaPlayerView` `scalePolicy` propriété de l&#39;objet. La stratégie `MediaPlayerView`d&#39;échelle par défaut est définie avec une instance de la `MaintainAspectRatioScalePolicy` classe. Pour réinitialiser la stratégie d&#39;échelle, remplacez l&#39;instance par défaut de `MaintainAspectRatioScalePolicy` on `MediaPlayerView.scalePolicy` par votre propre stratégie. (Vous ne pouvez pas définir la `scalePolicy` propriété sur une valeur nulle.)

1. Implémentez l’ `MediaPlayerViewScalePolicy` interface pour créer votre propre stratégie à l’échelle.

   Il `MediaPlayerViewScalePolicy` existe une méthode :

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK utilise un `StageVideo` objet pour l’affichage de la vidéo. Comme `StageVideo` les objets ne figurent pas sur la liste d’affichage, le `viewPort` paramètre contient les coordonnées absolues de la vidéo.
   >
   >
   >Par exemple:    >
   >
   >
   ```>
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
   >```   >
   >



1. Affectez votre mise en oeuvre à la `MediaPlayerView` propriété.

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. Ajouter votre vue à la `view` propriété du lecteur multimédia.

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

