---
description: Lorsque la lecture comprend de la publicité, le navigateur TVSDK envoie des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.
title: Ordre des événements publicitaires
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Ordre des événements publicitaires {#order-of-advertising-events}

Lorsque la lecture comprend de la publicité, le navigateur TVSDK envoie des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Lors de la lecture des publicités, l’ordre des événements est le suivant :

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* Les éléments suivants sont distribués pour chaque publicité de la coupure publicitaire :

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` (plusieurs fois pendant la lecture d’une publicité)
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

L’exemple suivant montre une progression type des événements de lecture publicitaire :

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```

