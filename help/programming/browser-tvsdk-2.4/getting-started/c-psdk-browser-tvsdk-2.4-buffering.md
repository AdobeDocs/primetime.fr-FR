---
description: Vous pouvez configurer des visuels pour avertir l’utilisateur que le contenu est mis en mémoire tampon.
title: Mise en mémoire tampon
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 3%

---


# Mise en mémoire tampon{#buffering}

Vous pouvez configurer des visuels pour avertir l’utilisateur que le contenu est mis en mémoire tampon.

Prêtez attention aux événements `AdobePSDK.PSDKEventType.BUFFERING_BEGIN` et `AdobePSDK.PSDKEventType.BUFFERING_END`. Par exemple :

```js
player.addEventListener(AdobePSDK.PSDKEventType.BUFFERING_BEGIN,  
                        function (event) { 
                            buffering = true; 
                            // add buffering layer 
                        }); 
  
player.addEventListener(AdobePSDK.PSDKEventType.BUFFERING_END,  
                        function (event) { 
                           buffering = false; 
                           // remove buffering layer 
                        });
```

La structure de l’interface utilisateur fournit une implémentation par défaut du comportement d’incrustation de mise en mémoire tampon, qui peut être étendue comme illustré ci-dessous :

```js
// Using UI Framework 
function myBufferingOverlayBehavior (element, configuration, player, localize, baseLog) { 
    return ptp.bufferingOverlayBehavior(element, configuration, player, localize, baseLog); 
} 
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
        mediaResource:'Specify Resource URL', 
        bufferingOverlay: { 
            behavior: myBufferingOverlayBehavior, 
            classNames: 'ptp-buffering-overlay my_buffering_overlay_bar' 
        } 
    } 
 
}); 
```

Voici à quoi ressemble le DOM obtenu :

```
<div id=" videoDiv" class="ptp-root-element"> 
<div name="videoPlayer" value="videoPlayer" class="ptp-main-video-div-style"> 
<div name="bufferingOverlay" value="bufferingOverlay" class="ptp-buffering-overlay my_buffering_overlay_bar'"></div> 
</div> 
</div> 
```

