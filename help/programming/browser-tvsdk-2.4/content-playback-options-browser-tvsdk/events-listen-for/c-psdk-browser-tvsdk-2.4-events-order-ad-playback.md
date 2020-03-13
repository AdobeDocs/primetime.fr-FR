---
description: Lorsque votre lecture comprend de la publicité, le navigateur TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.
seo-description: Lorsque votre lecture comprend de la publicité, le navigateur TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.
seo-title: 'Ordre des publicitaires '
title: 'Ordre des publicitaires '
uuid: 9787e6ac-5e52-4d7d-8fc7-f7609633707c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ordre des publicitaires{#order-of-advertising-events}

Lorsque votre lecture comprend de la publicité, le navigateur TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Lors de la lecture des publicités, l’ordre des  est le suivant :

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* Les éléments suivants sont distribués pour chaque publicité de la coupure publicitaire :

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` (plusieurs fois pendant la lecture d’une publicité)
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

L’exemple suivant illustre une progression type du de lecture d’annonce :

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```

