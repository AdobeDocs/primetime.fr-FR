---
description: Vous pouvez afficher des légendes lors de la lecture de contenu vidéo.
title: Sous-titres
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# Sous-titres{#captions}

Vous pouvez afficher des légendes lors de la lecture de contenu vidéo.

Pour gérer les sous-titres, vous devez ajouter le `AdobePSDK.PSDKEventType.CAPTIONS_UPDATED` écouteur d’événement :

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

La structure de l’interface utilisateur fournit une implémentation des comportements de sous-titres par défaut, qui peut être modifiée. Les comportements de sous-titres codés peuvent également être modifiés en étendant les comportements de sous-titres codés par défaut. Par exemple :

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
