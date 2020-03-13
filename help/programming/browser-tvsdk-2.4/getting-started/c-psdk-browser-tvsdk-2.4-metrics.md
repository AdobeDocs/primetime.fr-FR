---
description: Le SDK du navigateur fournit des mesures à utiliser pour l’analyse et le débogage. Vous pouvez obtenir ces mesures à l’aide de QoSProvider.
seo-description: Le SDK du navigateur fournit des mesures à utiliser pour l’analyse et le débogage. Vous pouvez obtenir ces mesures à l’aide de QoSProvider.
seo-title: Mesures
title: Mesures
uuid: 4734e532-1f83-4691-b1bd-785f78e55d8d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mesures{#metrics}

Le SDK du navigateur fournit des mesures à utiliser pour l’analyse et le débogage. Vous pouvez obtenir ces mesures à l’aide de QoSProvider.

Par exemple :

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```

