---
title: Chaîne de licence
description: Chaîne de licence
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Chaîne de licence {#license-chaining}

Si la stratégie utilisée pour générer la licence prend en charge le chaînage des licences, le serveur doit décider s’il doit émettre une licence Leaf, une licence Root ou les deux. Pour déterminer le type de licence pris en charge par une stratégie, utilisez `Policy.getLicenseChainType()` ou appelez `Policy.getRootLicenseId()` pour déterminer si la stratégie possède une licence racine. Avec Adobe Access 2.0 chaînage des licences, le serveur émet généralement une licence feuille la première fois que l&#39;utilisateur demande une licence pour un ordinateur particulier et une licence racine par la suite. Pour déterminer si l&#39;ordinateur dispose déjà d&#39;une licence feuille pour la stratégie spécifiée, appelez `LicenseRequestMessage.clientHasLeafForPolicy()`.
