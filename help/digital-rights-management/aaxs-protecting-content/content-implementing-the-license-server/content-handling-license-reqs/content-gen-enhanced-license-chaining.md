---
title: Chaîne de licence améliorée
description: Chaîne de licence améliorée
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Chaînage de licence amélioré {#enhanced-license-chaining}

Avec un chaînage de licence amélioré dans Adobe Access 3.0, il est recommandé d&#39;émettre à la fois un Leaf et un Root la première fois que l&#39;utilisateur demande une licence pour un ordinateur particulier. Si l’utilisateur dispose déjà de la licence racine, le serveur ne peut émettre qu’un Leaf (appelez `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` pour déterminer si le client dispose déjà d’une racine améliorée de 3.0). Pour les demandes de licence ultérieures, le client indique qu’il dispose déjà d’une feuille et d’une racine, de sorte que le serveur doit émettre une nouvelle licence racine. Lorsque le chaînage de licences amélioré est utilisé, `setRootKeyRetrievalInfo()` doit être appelé pour fournir les informations d’identification nécessaires au déchiffrement de la clé de chiffrement racine dans la stratégie.

>[!NOTE]
>
>Si la stratégie prend en charge le chaînage de licences amélioré 3.0, mais que le client est Adobe Access 2.0, le serveur émettra une licence chaînée originale 2.0. Pour déterminer la version du client, utilisez LicenseRequestMessage.getClientVersion().

