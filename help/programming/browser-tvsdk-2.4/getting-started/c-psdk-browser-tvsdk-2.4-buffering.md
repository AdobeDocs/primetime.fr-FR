---
description: Vous pouvez configurer des visuels pour informer l’utilisateur que le contenu est mis en mémoire tampon.
seo-description: Vous pouvez configurer des visuels pour informer l’utilisateur que le contenu est mis en mémoire tampon.
seo-title: Mise en mémoire tampon
title: Mise en mémoire tampon
uuid: da9498ee-c736-4093-97a2-250d3ad56d49
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise en mémoire tampon{#buffering}

Vous pouvez configurer des visuels pour informer l’utilisateur que le contenu est mis en mémoire tampon.

Écoutez `AdobePSDK.PSDKEventType.BUFFERING_BEGIN` et `AdobePSDK.PSDKEventType.BUFFERING_END` . Par exemple :

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

