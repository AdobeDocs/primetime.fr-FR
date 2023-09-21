---
description: Le navigateur TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques QoS, tels que la mise en mémoire tampon et la recherche d’événements.
title: Événements QoS
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Événements QoS{#qos-events}

Le navigateur TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques QoS, tels que la mise en mémoire tampon et la recherche d’événements.

Pour être averti de tous les événements liés à QoS, créez une instance de `AdobePSDK.QOSProvider` et joindre l’instance MediaPlayer à celle-ci `QOSProvider` instance :

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Configurez un minuteur dans votre application pour vérifier régulièrement la variable `playbackInformation` de la propriété `qosProvider` instance. La variable `playbackInformation` fournit un instantané des statistiques de lecture actuelles. Par exemple :

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```
