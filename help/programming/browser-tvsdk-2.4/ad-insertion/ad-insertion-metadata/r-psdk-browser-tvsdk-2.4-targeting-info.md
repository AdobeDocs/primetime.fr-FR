---
description: Dans la prise de décision publicitaire Adobe Primetime, vous pouvez  des publicités sur des paires clé-valeur.
seo-description: Dans la prise de décision publicitaire Adobe Primetime, vous pouvez  des publicités sur des paires clé-valeur.
seo-title: Informations de ciblage
title: Informations de ciblage
uuid: 72114bef-36a1-4f2d-92e8-59f4885d70d2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Informations de ciblage{#targeting-information}

Dans la prise de décision publicitaire Adobe Primetime, vous pouvez  des publicités sur des paires clé-valeur.

Pour transmettre ces paires clé-valeur au navigateur TVSDK :

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```

