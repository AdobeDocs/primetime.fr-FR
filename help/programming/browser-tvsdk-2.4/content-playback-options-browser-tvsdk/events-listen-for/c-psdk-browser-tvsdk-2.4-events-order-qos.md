---
description: Le navigateur TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’ susceptibles d’influencer le calcul des statistiques de qualité de service (telles que la mise en mémoire tampon et la recherche d’un  de qualité de service).
seo-description: Le navigateur TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’ susceptibles d’influencer le calcul des statistiques de qualité de service (telles que la mise en mémoire tampon et la recherche d’un  de qualité de service).
seo-title: ' QoS'
title: ' QoS'
uuid: 3384bc51-b435-4cd9-a1f8-9abf2605205b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


#  QoS{#qos-events}

Le navigateur TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’ susceptibles d’influencer le calcul des statistiques de qualité de service (telles que la mise en mémoire tampon et la recherche d’un  de qualité de service).

Pour être averti de tous les  de liés à la qualité de service, créez une instance de `AdobePSDK.QOSProvider` et joignez l’instance MediaPlayer à cette `QOSProvider` instance :

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Configurez un minuteur dans votre application pour vérifier régulièrement la `playbackInformation` propriété de l’ `qosProvider` instance. La `playbackInformation` propriété fournit un instantané des statistiques de lecture actuelles. Par exemple :

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```

