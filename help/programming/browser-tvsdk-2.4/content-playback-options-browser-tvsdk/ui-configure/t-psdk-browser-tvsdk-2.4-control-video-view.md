---
description: Vous pouvez contrôler la position et la taille du vidéo à l’aide de l’objet MediaPlayerView.
seo-description: Vous pouvez contrôler la position et la taille du vidéo à l’aide de l’objet MediaPlayerView.
seo-title: 'Contrôle de la position et de la taille du vidéo '
title: 'Contrôle de la position et de la taille du vidéo '
uuid: d09dbc18-1ec0-4336-bf3f-7ff6c265c443
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Contrôle de la position et de la taille du vidéo{#control-the-position-and-size-of-the-video-view}

Vous pouvez contrôler la position et la taille du vidéo à l’aide de l’objet MediaPlayerView.

Par défaut, le navigateur TVSDK tente de conserver les proportions du vidéo chaque fois que la taille ou la position de la vidéo change en raison d’une modification apportée par l’application, d’un commutateur de  de, d’un commutateur de contenu, etc.

Vous pouvez remplacer le comportement des proportions par défaut en spécifiant une stratégie *d’*&#x200B;échelle différente. Spécifiez la stratégie d’échelle à l’aide de la `MediaPlayerView` `scalePolicy` propriété de l’objet. La stratégie d’échelle par défaut de `MediaPlayerView` est définie avec une instance de la `MaintainAspectRatioScalePolicy` classe. Pour réinitialiser la stratégie d’échelle, remplacez l’instance par défaut de `MaintainAspectRatioScalePolicy` on par `MediaPlayerView.scalePolicy` votre propre stratégie.

>[!IMPORTANT]
>
>Vous ne pouvez pas définir la `scalePolicy` propriété sur une valeur nulle.

## Scénarios de secours non Flash {#non-flash-fallback-scenarios}

Dans les scénarios de secours autres que Flash, pour que la stratégie d’échelle fonctionne correctement, l’élément div vidéo donné dans le `View` constructeur doit renvoyer des valeurs non nulles pour `offsetWidth` et `offsetHeight`. Pour donner un exemple de fonction incorrecte, lorsque la largeur et la hauteur des éléments div vidéo ne sont pas explicitement définies dans css, le `View` constructeur renvoie zéro pour `offsetWidth` ou `offsetHeight`.

>[!NOTE]
>
>CustomScalePolicy ne prend pas en charge certains navigateurs, notamment IE, Edge et Safari 9. Pour ces navigateurs, les proportions natives de la vidéo ne peuvent pas être modifiées. Toutefois, la position et les dimensions de la vidéo seront appliquées conformément à la stratégie d’échelle.

1. Implémentez l’ `MediaPlayerViewScalePolicy` interface pour créer votre propre stratégie d’échelle.

   Il `MediaPlayerViewScalePolicy` existe une méthode :

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

   Par exemple :

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

1. Affectez votre implémentation à la `MediaPlayerView` propriété.

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. Ajouter votre  à la `view` propriété du lecteur multimédia.

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**Par exemple : Mettez la vidéo à l’échelle pour remplir toute la  vidéo, sans conserver les proportions :**

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

