---
description: Le navigateur TVSDK fournit des mesures à utiliser pour l’analyse et le débogage. Vous pouvez obtenir ces mesures à l’aide de QoSProvider.
title: Mesures
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---

# Mesures{#metrics}

Le navigateur TVSDK fournit des mesures à utiliser pour l’analyse et le débogage. Vous pouvez obtenir ces mesures à l’aide de QoSProvider.

Par exemple :

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```
