---
description: Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView .
title: Contrôle de la position et de la taille de l’affichage vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Contrôle de la position et de la taille de l’affichage vidéo{#control-the-position-and-size-of-the-video-view}

Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView .

Par défaut, le navigateur TVSDK tente de conserver les proportions de l’affichage vidéo chaque fois que la taille ou la position de la vidéo change en raison d’une modification apportée par l’application, d’un commutateur de profil, d’un commutateur de contenu, etc.

Vous pouvez remplacer le comportement des proportions par défaut en spécifiant un autre *stratégie d&#39;échelle*. Définissez la stratégie de mise à l’échelle à l’aide du `MediaPlayerView` de `scalePolicy` . La stratégie d’échelle par défaut de `MediaPlayerView` est défini avec une instance de la variable `MaintainAspectRatioScalePolicy` classe . Pour réinitialiser la stratégie d’échelle, remplacez l’instance par défaut de `MaintainAspectRatioScalePolicy` on `MediaPlayerView.scalePolicy` avec votre propre politique.

>[!IMPORTANT]
>
>Vous ne pouvez pas définir la variable `scalePolicy` à une valeur nulle.

## Scénarios de secours autres que Flash {#non-flash-fallback-scenarios}

Dans les scénarios de secours autres que les Flashs, pour que la stratégie de mise à l’échelle fonctionne correctement, l’élément div vidéo indiqué dans la variable `View` le constructeur doit renvoyer des valeurs non nulles pour `offsetWidth` et `offsetHeight`. Pour donner un exemple de fonction incorrecte, lorsque la largeur et la hauteur des éléments div vidéo ne sont pas définies explicitement dans css, la fonction `View` constructeur renvoie zéro pour `offsetWidth` ou `offsetHeight`.

>[!NOTE]
>
>CustomScalePolicy ne prend pas en charge quelques navigateurs, notamment IE, Edge et Safari 9. Pour ces navigateurs, les proportions natives de la vidéo ne peuvent pas être modifiées. Toutefois, la position et les dimensions de la vidéo seront appliquées conformément à la stratégie de mise à l’échelle.

1. Mettez en oeuvre le `MediaPlayerViewScalePolicy` pour créer votre propre stratégie à l’échelle.

   La variable `MediaPlayerViewScalePolicy` possède une méthode :

   ```js
   /** 
   * Adjust the specified rectangle to match the new video dimensions. 
   * @param viewPort {AdobePSDK.Rectangle}The video rectangle as absolute position. 
   * @param videoWidth {Number}The video width. 
   * @param videoHeight {Number} The video height. 
   * @return {AdobePSDK.Rectangle} an adjusted rectangle. 
   */ 
   function adjustCallbackFunc(viewPort, videoWidth, videoHeight);
   ```

   Par exemple :

   ```js
   /** 
   Default Constructor 
   */ 
   MediaPlayerViewCustomScalePolicy = function() { 
       return this; 
   }; 
   MediaPlayerViewCustomScalePolicy.prototype = { 
       constructor: MediaPlayerViewScalePolicy, 
       adjustCallbackFunc: function(viewPort, videoWidth, videoHeight) { 
           /* Your Custom Adjustment here. */ 
           [...] 
           return adjustedRectangle; 
       } 
   };
   ```

1. Affectez votre mise en oeuvre au `MediaPlayerView` .

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. Ajoutez votre vue au `view` .

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**Par exemple : mettez la vidéo à l’échelle pour remplir l’ensemble de l’affichage vidéo, sans conserver les proportions :**

```
/** 
 * Default constructor. 
 */ 
MediaPlayerViewCustomScalePolicy = function() { 
    return this; 
}; 
MediaPlayerViewCustomScalePolicy.prototype = { 
    constructor: MediaPlayerViewScalePolicy, 
    /** 
    * A very simple custom scale policy - the video will fill the entire 
    * allocated space. The aspect ratio will not be kept. 
    */ 
    adjustCallbackFunc: function(viewPort, videoWidth, videoHeight) { 
        return viewPort; 
    } 
}; 
var view = new AdobePSDK.MediaPlayerView(videoDiv); 
view.scalePolicy = new MediaPlayerViewCustomScalePolicy (); 
mediaPlayer.view = view;
```
