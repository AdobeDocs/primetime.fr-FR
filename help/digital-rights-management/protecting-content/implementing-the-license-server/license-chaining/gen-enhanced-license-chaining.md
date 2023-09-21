---
title: Chaîne de licence améliorée
description: Chaîne de licence améliorée
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Chaîne de licence améliorée {#enhanced-license-chaining}

Si une stratégie DRM est utilisée pour générer une licence prenant en charge le chaînage de licences, le serveur doit décider s’il émet une licence Leaf, une licence Root, ou les deux. Si vous souhaitez déterminer le type de licence pris en charge par une stratégie DRM, vous devez utiliser `Policy.getLicenseChainType()`, ou appelez `Policy.getRootLicenseId()` pour déterminer si la stratégie DRM possède une licence racine. Avec le chaînage de licences Adobe Primetime DRM 2.0, le serveur émet généralement une licence feuille la première fois qu’un utilisateur demande une licence pour un ordinateur particulier et une licence racine par la suite. Si vous souhaitez déterminer si la machine dispose déjà d’une licence feuille pour la stratégie spécifiée, vous devez appeler `LicenseRequestMessage.clientHasLeafForPolicy()`.

Avec un chaînage de licence amélioré dans Adobe Primetime DRM 3.0, il est recommandé d’émettre à la fois une feuille et une racine la première fois que l’utilisateur demande une licence pour un ordinateur particulier. Si l’utilisateur dispose déjà de la licence Root, le serveur ne peut émettre qu’un Leaf (appel `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` pour déterminer si le client dispose déjà d’une racine améliorée 3.0). Pour les demandes de licence ultérieures, le client indique alors qu’il dispose déjà d’une feuille et d’une racine, de sorte que le serveur doit émettre une nouvelle licence Root. Lorsque le chaînage de licence amélioré est utilisé, `setRootKeyRetrievalInfo()` doit être appelé pour fournir les informations d’identification nécessaires pour déchiffrer la clé de chiffrement racine dans la stratégie DRM.

>[!NOTE]
>
>Si la stratégie prend en charge le chaînage de licences amélioré 3.0, mais que le client est Primetime DRM 2.0, le serveur émet alors une licence chaînée d’origine 2.0. Pour déterminer la version du client, utilisez `LicenseRequestMessage.getClientVersion()`.
