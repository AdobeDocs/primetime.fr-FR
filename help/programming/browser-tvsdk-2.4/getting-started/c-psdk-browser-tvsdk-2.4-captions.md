---
description: Vous pouvez afficher des légendes lors de la lecture de contenu vidéo.
seo-description: Vous pouvez afficher des légendes lors de la lecture de contenu vidéo.
seo-title: Légendes
title: Légendes
uuid: 4dedcedc-50e5-4983-bb09-3f316337117e
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 3%

---


# Légendes{#captions}

Vous pouvez afficher des légendes lors de la lecture de contenu vidéo.

Pour gérer les légendes, vous devez ajouter l’écouteur de `AdobePSDK.PSDKEventType.CAPTIONS_UPDATED` événement :

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.CAPTIONS_UPDATED,  
                        onCaptionsUpdateEvent); 
... 
function onCaptionsUpdateEvent (event) { 
  // code to show the captions icon and any settings button. 
<pre>
   For example: 
  var btnCC = document.getElementById("btn_captions"); 
   btnCC.classList.remove("invisible"); 
   
  var btnSettings = document.getElementById("btn_settings"); 
   btnSettings.classList.remove("invisible"); 
 } 
</pre>
```

La structure de l’interface utilisateur fournit une implémentation par défaut des comportements de sous-titrage, qui peut être modifiée. Les comportements de sous-titrage peuvent également être modifiés en étendant les comportements de sous-titrage par défaut. Par exemple :

```js
// Using UI Framework 
var playerWrapper = ptp.videoPlayer(‘.videoDiv', { 
player:{ 
    mediaResource: 'Specify Resource URL', 
    ccStyle: { 
    font:AdobePSDK.TextFormat.CURSIVE, 
    fontColor:AdobePSDK.TextFormat.BRIGHT_WHITE, 
    edgeColor:AdobePSDK.TextFormat.BLUE, 
    backgroundColor:AdobePSDK.TextFormat.BLACK, 
    fillColor:AdobePSDK.TextFormat.BLUE, 
    size:AdobePSDK.TextFormat.MEDIUM, 
    fontOpacity:100, 
    backgroundOpacity:1, 
    fillOpacity:1 
   } 
 } 
 
}); 
```
