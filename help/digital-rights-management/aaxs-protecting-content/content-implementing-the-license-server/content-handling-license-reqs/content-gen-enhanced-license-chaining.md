---
title: Chaîne de licence améliorée
description: Chaîne de licence améliorée
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Chaîne de licence améliorée {#enhanced-license-chaining}

Avec un chaînage de licence amélioré dans Adobe Access 3.0, il est recommandé d’émettre à la fois une feuille et une racine la première fois que l’utilisateur demande une licence pour un ordinateur particulier. Si l’utilisateur dispose déjà de la licence Root, le serveur ne peut émettre qu’un Leaf (appel `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` pour déterminer si le client dispose déjà d’une racine améliorée 3.0). Pour les demandes de licence ultérieures, le client indique qu’il dispose déjà d’une feuille et d’une racine, de sorte que le serveur doit émettre une nouvelle licence Root. Lorsque le chaînage de licence amélioré est utilisé, `setRootKeyRetrievalInfo()` doit être appelé pour fournir les informations d’identification nécessaires au déchiffrement de la clé de chiffrement racine dans la stratégie.

>[!NOTE]
>
>Si la stratégie prend en charge le chaînage de licences amélioré 3.0, mais que le client est Adobe Access 2.0, le serveur émet une licence chaînée d’origine 2.0. Pour déterminer la version du client, utilisez LicenseRequestMessage.getClientVersion().
