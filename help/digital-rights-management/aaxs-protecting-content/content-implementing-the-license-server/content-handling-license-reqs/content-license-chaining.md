---
seo-title: Chaîne de licence
title: Chaîne de licence
uuid: dcc12663-ef9e-4c73-b837-66fcec39358b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Chaîne de licence{#license-chaining}

Si la stratégie utilisée pour générer la licence prend en charge le chaînage des licences, le serveur doit décider s’il doit émettre une licence Leaf, une licence Root ou les deux. Pour déterminer le type de licence prise en charge, d’utilisation `Policy.getLicenseChainType()`ou `Policy.getRootLicenseId()` d’appel d’une stratégie pour déterminer si celle-ci possède une licence racine. Avec le chaînage de licences Adobe Access 2.0, le serveur émet généralement une licence feuille la première fois que l&#39;utilisateur demande une licence pour un ordinateur particulier et une licence racine par la suite. Pour déterminer si l&#39;ordinateur dispose déjà d&#39;une licence feuille pour la stratégie spécifiée, appelez `LicenseRequestMessage.clientHasLeafForPolicy()`.
