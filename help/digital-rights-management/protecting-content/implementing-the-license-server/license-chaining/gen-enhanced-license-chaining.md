---
title: Chaîne de licence améliorée
description: Chaîne de licence améliorée
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Chaînage de licence amélioré {#enhanced-license-chaining}

Si une stratégie DRM est utilisée pour générer une licence qui prend en charge le chaînage de licences, le serveur doit décider s’il doit émettre une licence Leaf, une licence Root, ou les deux. Si vous souhaitez déterminer le type de licence pris en charge par une stratégie DRM, vous devez utiliser `Policy.getLicenseChainType()` ou appeler `Policy.getRootLicenseId()` pour déterminer si la stratégie DRM possède une licence racine. Avec le chaînage de licences Adobe Primetime DRM 2.0, le serveur émet généralement une licence feuille la première fois qu&#39;un utilisateur demande une licence pour un ordinateur particulier et une licence racine par la suite. Si vous souhaitez déterminer si l&#39;ordinateur dispose déjà d&#39;une licence feuille pour la stratégie spécifiée, vous devez appeler `LicenseRequestMessage.clientHasLeafForPolicy()`.

Avec un chaînage de licence amélioré dans Adobe Primetime DRM 3.0, il est recommandé d&#39;émettre à la fois un Leaf et un Root la première fois que l&#39;utilisateur demande une licence pour un ordinateur particulier. Si l’utilisateur dispose déjà de la licence racine, le serveur ne peut émettre qu’un Leaf (appelez `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` pour déterminer si le client dispose déjà d’une racine améliorée de 3.0). Pour les demandes de licence ultérieures, le client indique alors qu’il dispose déjà d’une feuille et d’une racine, de sorte que le serveur doit émettre une nouvelle licence racine. Lorsque le chaînage de licences amélioré est utilisé, `setRootKeyRetrievalInfo()` doit être appelé pour fournir les informations d&#39;identification nécessaires pour déchiffrer la clé de chiffrement racine dans la stratégie DRM.

>[!NOTE]
>
>Si la stratégie prend en charge le chaînage de licences amélioré 3.0, mais que le client est Primetime DRM 2.0, le serveur émet alors une licence chaînée originale 2.0. Pour déterminer la version du client, utilisez `LicenseRequestMessage.getClientVersion()`.

