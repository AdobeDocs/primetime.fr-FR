---
description: En Adobe Primetime, vous pouvez cible des publicités sur des paires clé-valeur.
title: Informations de ciblage
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---


# Informations de ciblage{#targeting-information}

En Adobe Primetime, vous pouvez cible des publicités sur des paires clé-valeur.

Pour transmettre ces paires clé-valeur au navigateur TVSDK :

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```

