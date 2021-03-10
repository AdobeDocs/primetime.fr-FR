---
description: Le navigateur TVSDK fournit des mesures à utiliser pour l’analyse et le débogage. Vous pouvez obtenir ces mesures à l’aide de QoSProvider.
title: Mesures
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 5%

---


# Mesures{#metrics}

Le navigateur TVSDK fournit des mesures à utiliser pour l’analyse et le débogage. Vous pouvez obtenir ces mesures à l’aide de QoSProvider.

Par exemple :

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```

