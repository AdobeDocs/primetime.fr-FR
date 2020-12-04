---
description: Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.
seo-description: Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.
seo-title: Contrôle de la position et de la taille de la vue vidéo
title: Contrôle de la position et de la taille de la vue vidéo
uuid: d09dbc18-1ec0-4336-bf3f-7ff6c265c443
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---


# Contrôler la position et la taille de la vue vidéo{#control-the-position-and-size-of-the-video-view}

Vous pouvez contrôler la position et la taille de la vue vidéo à l’aide de l’objet MediaPlayerView.

Par défaut, le navigateur TVSDK tente de conserver les proportions de la vue vidéo chaque fois que la taille ou la position de la vidéo change en raison d’une modification apportée par l’application, d’un commutateur de profil, d’un commutateur de contenu, etc.

Vous pouvez remplacer le comportement par défaut des proportions en spécifiant une autre *stratégie d’échelle*. Spécifiez la stratégie d&#39;échelle à l&#39;aide de la propriété `scalePolicy` de l&#39;objet `MediaPlayerView`. La stratégie d&#39;échelle par défaut de `MediaPlayerView` est définie avec une instance de la classe `MaintainAspectRatioScalePolicy`. Pour réinitialiser la stratégie d&#39;échelle, remplacez l&#39;instance par défaut de `MaintainAspectRatioScalePolicy` sur `MediaPlayerView.scalePolicy` par votre propre stratégie.

>[!IMPORTANT]
>
>Vous ne pouvez pas définir la propriété `scalePolicy` sur une valeur nulle.

## Scénarios de reprise non Flash {#non-flash-fallback-scenarios}

Dans les scénarios de secours autres que Flash, pour que la stratégie d&#39;échelle fonctionne correctement, l&#39;élément div vidéo donné dans le constructeur `View` doit renvoyer des valeurs non nulles pour `offsetWidth` et `offsetHeight`. Pour donner un exemple de fonction incorrecte, parfois lorsque la largeur et la hauteur des éléments div vidéo ne sont pas définies explicitement dans css, le constructeur `View` renvoie zéro pour `offsetWidth` ou `offsetHeight`.

>[!NOTE]
>
>CustomScalePolicy ne prend pas en charge certains navigateurs, notamment IE, Edge et Safari 9. Pour ces navigateurs, les proportions natives de la vidéo ne peuvent pas être modifiées. Cependant, la position et les dimensions de la vidéo seront appliquées conformément à la stratégie d&#39;échelle.

1. Implémentez l&#39;interface `MediaPlayerViewScalePolicy` pour créer votre propre stratégie d&#39;échelle.

   Le `MediaPlayerViewScalePolicy` comporte une méthode :

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

1. Affectez votre implémentation à la propriété `MediaPlayerView`.

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. Ajoutez votre vue à la propriété `view` du lecteur multimédia.

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**Par exemple : Mettez la vidéo à l’échelle pour remplir toute la vue vidéo, sans conserver les proportions :**

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

