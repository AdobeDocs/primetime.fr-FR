---
description: Lorsque votre lecture comprend de la publicité, TVSDK distribue des événements/notifications dans les séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.
title: Ordre des événements publicitaires
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Ordre des événements publicitaires{#order-of-advertising-events}

Lorsque votre lecture comprend de la publicité, TVSDK distribue des événements/notifications dans les séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Lors de la lecture de publicités, l’ordre des événements est le suivant :

* `AdBreakPlaybackEvent.AD_BREAK_STARTED`
* Les éléments suivants sont distribués pour chaque publicité dans la coupure publicitaire :

   * `AdPlaybackEvent.AD_STARTED`
   * `AdPlaybackEvent.AD_PROGRESS` (plusieurs fois pendant la lecture d’une publicité)
   * `AdClickEvent.AD_CLICK` (pour chaque clic)
   * `AdPlaybackEvent.AD_COMPLETED`

* `AdBreakPlaybackEvent.AD_BREAK_COMPLETED`

L’exemple suivant illustre une progression type des événements de lecture de publicité :

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
