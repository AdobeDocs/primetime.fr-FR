---
seo-title: Chaîne de licence améliorée
title: Chaîne de licence améliorée
uuid: f869b4e7-4b24-4832-94a7-b7143567ab58
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Chaîne de licence améliorée {#enhanced-license-chaining}

Si une stratégie DRM est utilisée pour générer une licence prenant en charge le chaînage de licences, le serveur doit décider s’il doit émettre une licence Leaf, une licence Root ou les deux. Si vous souhaitez déterminer le type de licence pris en charge par une stratégie DRM, vous devez utiliser `Policy.getLicenseChainType()`ou appeler `Policy.getRootLicenseId()` pour déterminer si la stratégie DRM comporte une licence racine. Avec le chaînage de licences Adobe Primetime DRM 2.0, le serveur émet généralement une licence feuille la première fois qu’un utilisateur demande une licence pour un ordinateur particulier et une licence racine par la suite. Si vous souhaitez déterminer si l’ordinateur dispose déjà d’une licence feuille pour la stratégie spécifiée, vous devez appeler `LicenseRequestMessage.clientHasLeafForPolicy()`.

Grâce au chaînage de licences amélioré dans Adobe Primetime DRM 3.0, il est recommandé d’émettre une feuille et une racine la première fois que l’utilisateur demande une licence pour un ordinateur particulier. Si l’utilisateur dispose déjà de la licence racine, le serveur ne peut émettre qu’une feuille (appel `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` pour déterminer si le client dispose déjà d’une racine améliorée 3.0). Pour les demandes de licence suivantes, le client indique alors qu’il dispose déjà d’une feuille et d’une racine, de sorte que le serveur doit émettre une nouvelle licence racine. Lorsque le chaînage de licence amélioré est utilisé, `setRootKeyRetrievalInfo()` vous devez appeler pour fournir les informations d’identification nécessaires au déchiffrement de la clé de chiffrement racine dans la stratégie DRM.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Si la stratégie prend en charge le chaînage de licences amélioré 3.0, mais que le client est Primetime DRM 2.0, le serveur émet alors une licence chaînée d’origine 2.0. Pour déterminer la version du client, utilisez `LicenseRequestMessage.getClientVersion()`.

