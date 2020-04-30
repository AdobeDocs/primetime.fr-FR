---
description: 'null'
seo-description: 'null'
seo-title: Création d’un lecteur de base à l’aide de l’interface utilisateur
title: Création d’un lecteur de base à l’aide de l’interface utilisateur
uuid: d1a82dbb-1c05-4d0c-b6bc-e07cbede93cb
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Création d’un lecteur de base à l’aide de l’interface utilisateur{#create-a-basic-player-using-the-ui-framework}

Pour créer un lecteur de base à l’aide de l’interface utilisateur :

1. Créez une instance `<div>` pour votre lecteur.

   Par exemple :

   ```
   <div id="video1" > 
    </div>
   ```

1. Chargez le lecteur.

   ```js
   <script> 
       (function(){ 
           var player = ptp.videoPlayer('#video1'); 
       })(); 
   </script>
   ```

   Lors de la création du lecteur, une classe CSS de `<div>` l’élément `ptp-main-video-div-style`spécifié est attribuée à l’élément spécifié. Le modèle DOM obtenu ressemble à ceci :

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <video class="vp-video-element"></video> 
   </div>
   ```

1. Ajouter un contrôle d’interface utilisateur.

   Par exemple, ajoutez une barre de contrôle qui s’affiche lorsque la souris passe sur le lecteur :

   ```js
   <script> 
       (function(){ 
           function myControlBarBehavior(element, configuration, player) { 
               return ptp.controlBarBehavior(element, configuration, player); 
           } 
           var player = ptp.videoPlayer('#video1', { 
               controlBar: { 
                   behavior: myControlBarBehavior, 
                   classNames: 'ptp-control-bar my_control_bar' 
               } 
           }); 
       })(); 
   </script>
   ```

   Le DOM résultant s’affiche comme suit :

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <div class="ptp-control-bar my_control_bar"></div> 
       <video class="vp-video-element"></video> 
   </div>
   ```

L’objet renvoyé par appel `ptp.videoPlayer()` fournit un comportement qui encapsule l’API du lecteur multimédia TVSDK et permet le contrôle programmatique de la lecture. Lorsque vous effectuez des appels sur l’instance du lecteur multimédia, l’interface utilisateur se met à jour en fonction des événements déclenchés par le lecteur multimédia :

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
