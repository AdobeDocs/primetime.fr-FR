---
description: Dans Adobe Primetime Ad Decisioning, vous pouvez cibler des publicités sur des paires clé-valeur.
title: Informations sur le ciblage
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---

# Informations sur le ciblage{#targeting-information}

Dans Adobe Primetime Ad Decisioning, vous pouvez cibler des publicités sur des paires clé-valeur.

Pour transmettre ces paires clé-valeur au Browser TVSDK :

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```
