---
description: Lorsque votre lecture comprend de la publicité, le navigateur TVSDK distribue des événements/notifications dans les séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.
title: Ordre des événements publicitaires
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Ordre des événements publicitaires{#order-of-advertising-events}

Lorsque votre lecture comprend de la publicité, le navigateur TVSDK distribue des événements/notifications dans les séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Lors de la lecture de publicités, l’ordre des événements est le suivant :

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* Les éléments suivants sont distribués pour chaque publicité dans la coupure publicitaire :

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` (plusieurs fois pendant la lecture d’une publicité)
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

L’exemple suivant illustre une progression type des événements de lecture de publicité :

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```
