---
title: Création d’un lecteur de base à l’aide de l’interface utilisateur
description: Création d’un lecteur de base à l’aide de l’interface utilisateur
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 1%

---


# Créez un lecteur de base à l’aide de l’interface utilisateur Framework{#create-a-basic-player-using-the-ui-framework}

Pour créer un lecteur de base à l’aide de l’interface utilisateur :

1. Créez un `<div>` pour votre instance de lecteur.

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

   Lorsque le lecteur est créé, l’élément `<div>` spécifié se voit attribuer une classe CSS `ptp-main-video-div-style`. Le modèle DOM obtenu ressemble à ceci :

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <video class="vp-video-element"></video> 
   </div>
   ```

1. Ajoutez un contrôle d’interface utilisateur.

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

L’objet renvoyé par l’appel de `ptp.videoPlayer()` fournit un comportement qui encapsule l’API du lecteur multimédia TVSDK et permet le contrôle programmatique de la lecture. Lorsque vous effectuez des appels sur l’instance du lecteur multimédia, l’interface utilisateur se met à jour en fonction des événements déclenchés par le lecteur multimédia :

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
