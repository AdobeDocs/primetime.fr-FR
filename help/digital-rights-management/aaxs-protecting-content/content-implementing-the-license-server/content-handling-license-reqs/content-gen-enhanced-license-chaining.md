---
seo-title: Chaîne de licence améliorée
title: Chaîne de licence améliorée
uuid: dc0e0a46-d3cd-44e8-a45d-3e22787be44e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Chaîne de licence améliorée {#enhanced-license-chaining}

Avec un chaînage de licence amélioré dans Adobe Access 3.0, il est recommandé d&#39;émettre à la fois un Leaf et un Root la première fois que l&#39;utilisateur demande une licence pour un ordinateur particulier. Si l’utilisateur dispose déjà de la licence Root, le serveur ne peut émettre qu’un Leaf (appel `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` pour déterminer si le client dispose déjà d’une racine 3.0 Enhanced). Pour les demandes de licence ultérieures, le client indique qu’il dispose déjà d’une feuille et d’une racine, de sorte que le serveur doit émettre une nouvelle licence racine. Lorsque la chaîne de licence améliorée est utilisée, `setRootKeyRetrievalInfo()` vous devez appeler pour fournir les informations d’identification nécessaires au déchiffrement de la clé de chiffrement racine dans la stratégie.

>[!NOTE]
>
>Si la stratégie prend en charge le chaînage de licences amélioré 3.0, mais que le client est Adobe Access 2.0, le serveur émettra une licence chaînée originale 2.0. Pour déterminer la version du client, utilisez LicenseRequestMessage.getClientVersion().

