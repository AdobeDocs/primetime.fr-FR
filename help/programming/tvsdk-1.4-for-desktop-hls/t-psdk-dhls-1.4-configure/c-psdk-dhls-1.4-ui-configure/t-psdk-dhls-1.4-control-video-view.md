---
description: Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView .
title: Contrôle de la position et de la taille de l’affichage vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Contrôle de la position et de la taille de l’affichage vidéo{#control-the-position-and-size-of-the-video-view}

Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView .

TVSDK tente par défaut de conserver les proportions de l’affichage vidéo chaque fois que la taille ou la position de la vidéo change (en raison d’une modification apportée par l’application, ou par un commutateur de profil, ou un commutateur de contenu, etc.).

Vous pouvez remplacer le comportement des proportions par défaut en spécifiant un autre *stratégie d&#39;échelle*. Définissez la stratégie de mise à l’échelle à l’aide du `MediaPlayerView` de `scalePolicy` . La variable `MediaPlayerView`La stratégie d’échelle par défaut de est définie avec une instance de la variable `MaintainAspectRatioScalePolicy` classe . Pour réinitialiser la stratégie d’échelle, remplacez l’instance par défaut de `MaintainAspectRatioScalePolicy` on `MediaPlayerView.scalePolicy` avec votre propre politique. (Vous ne pouvez pas définir la variable `scalePolicy` à une valeur nulle.)

1. Mettez en oeuvre le `MediaPlayerViewScalePolicy` pour créer votre propre stratégie à l’échelle.

   La variable `MediaPlayerViewScalePolicy` possède une méthode :

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK utilise une `StageVideo` pour afficher la vidéo, et pour `StageVideo` ne figurent pas dans la liste d’affichage, la variable `viewPort` contient les coordonnées absolues de la vidéo.
   >
   >
   >Par exemple :
   >
   >```
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
   >

1. Affectez votre mise en oeuvre au `MediaPlayerView` .

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. Ajoutez votre vue au `view` .

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**Par exemple : mettez la vidéo à l’échelle pour remplir l’ensemble de l’affichage vidéo, sans conserver les proportions :**

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
