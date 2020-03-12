---
description: Lorsque votre lecture comprend de la publicité, TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.
seo-description: Lorsque votre lecture comprend de la publicité, TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.
seo-title: 'Ordre des publicitaires '
title: 'Ordre des publicitaires '
uuid: 34a6a606-2f2e-42de-88fd-c91202cafddf
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ordre des publicitaires{#order-of-advertising-events}

Lorsque votre lecture comprend de la publicité, TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Lors de la lecture des publicités, l’ordre des  est le suivant :

* `AdBreakPlaybackEvent.AD_BREAK_STARTED`
* Les éléments suivants sont distribués pour chaque publicité de la coupure publicitaire :

   * `AdPlaybackEvent.AD_STARTED`
   * `AdPlaybackEvent.AD_PROGRESS` (plusieurs fois pendant la lecture d’une publicité)
   * `AdClickEvent.AD_CLICK` (pour chaque clic)
   * `AdPlaybackEvent.AD_COMPLETED`

* `AdBreakPlaybackEvent.AD_BREAK_COMPLETED`

L’exemple suivant illustre une progression type du de lecture d’annonce :

```
mediaPlayer.addEventListener(AdBreakPlaybackEvent.AD_BREAK_STARTED, onAdBreakStarted); 
private function onAdBreakStarted(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    ... 
} 
mediaPlayer.addEventListener(AdBreakPlaybackEvent.AD_BREAK_COMPLETED, onAdBreakCompleted); 
private function onAdBreakCompleted(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_STARTED, onAdStarted); 
private function onAdStarted(event:AdPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_PROGRESS, onAdProgress); 
private function onAdProgress(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad;  
    var progress:uint = event.progress; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_COMPLETED, onAdCompleted); 
private function onAdCompleted(event:AdPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    ... 
} 
mediaPlayer.addEventListener(AdClickEvent.AD_CLICK, onAdClick); 
private function onAdClick(event:AdClickThroughEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    var info:AdClick = event.adClick; 
    ... 
} 
```

