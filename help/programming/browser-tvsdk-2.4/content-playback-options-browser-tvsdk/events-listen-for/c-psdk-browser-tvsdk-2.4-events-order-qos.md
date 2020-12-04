---
description: Le navigateur TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques de la qualité de service (QoS), comme la mise en mémoire tampon et la recherche de événements.
seo-description: Le navigateur TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques de la qualité de service (QoS), comme la mise en mémoire tampon et la recherche de événements.
seo-title: Événements QoS
title: Événements QoS
uuid: 3384bc51-b435-4cd9-a1f8-9abf2605205b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---


# Événements QoS{#qos-events}

Le navigateur TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques de la qualité de service (QoS), comme la mise en mémoire tampon et la recherche de événements.

Pour être informé de tous les événements liés à la qualité de service, créez une instance de `AdobePSDK.QOSProvider` et joignez l’instance MediaPlayer à cette instance `QOSProvider` :

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Configurez un minuteur dans votre application pour vérifier périodiquement la propriété `playbackInformation` de l&#39;instance `qosProvider`. La propriété `playbackInformation` fournit un instantané des statistiques de lecture actuelles. Par exemple :

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```

