---
title: Chaîne de licence
description: Chaîne de licence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Chaîne de licence{#license-chaining}

Si la stratégie utilisée pour générer la licence prend en charge le chaînage des licences, le serveur doit décider s’il émet une licence Leaf, une licence Root, ou les deux. Pour déterminer le type de licence pris en charge par une stratégie, utilisez `Policy.getLicenseChainType()`, ou appelez `Policy.getRootLicenseId()` pour déterminer si la stratégie possède une licence racine. Avec le chaînage de licences Adobe Access 2.0, le serveur émet généralement une licence feuille la première fois que l’utilisateur demande une licence pour un ordinateur particulier et une licence racine par la suite. Pour déterminer si la machine dispose déjà d’une licence feuille pour la stratégie spécifiée, appelez `LicenseRequestMessage.clientHasLeafForPolicy()`.
