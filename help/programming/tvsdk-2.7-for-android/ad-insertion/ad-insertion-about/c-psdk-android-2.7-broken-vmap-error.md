---
description: Lorsque TVSDK rencontre une VMAP endommagée dans une réponse du serveur de publicités, il envoie une erreur 1109 (NETWORK_AD_URL_FAILED).
keywords: 1109;NETWORK_AD_URL_FAILED;VMAP endommagée
title: Gestion des erreurs du client pour VMAP endommagée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Gestion des erreurs du client pour VMAP endommagée {#client-error-handling-for-broken-vmap}

Lorsque TVSDK rencontre une VMAP endommagée dans une réponse du serveur de publicités, il envoie une erreur 1109 (NETWORK_AD_URL_FAILED).

Selon la nature de la réponse du serveur de publicités et les paramètres de chargement de la publicité, votre lecteur peut recevoir différents nombres d’erreurs 1109 lorsque TVSDK rencontre un VMAP endommagé dans une réponse du serveur de publicités.

Examinons un scénario dans lequel la réponse du serveur d’annonces pointe vers le code XML VMAP. Supposons également que la réponse du serveur d’annonces comporte quatre emplacements d’annonces disponibles, chacun pointant vers le même VMAP. Enfin, supposons que ce VMAP soit rompu.

Dans ce scénario, si la résolution de publicité différée est activée ( [Activation de la résolution des publicités différées](../../../tvsdk-2.7-for-android/ad-insertion/c-psdk-android-2.7-lazy-ad-resolving/t-psdk-android-2.7-enable-lazy-ad-resolving.md)), TVSDK enverra deux erreurs 109 (pas une comme prévu) : une erreur est envoyée à chaque analyse au-dessus de la chronologie. En effet, lorsque la résolution différée des publicités est activée, TVSDK analyse les publicités en 2 passages : la première passe se produit juste avant que la lecture du contenu ne commence pour les publicités preroll, et la seconde passe après le démarrage de la lecture pour les publicités mid-roll et post-roll.

>[!NOTE]
>
>Dans ce scénario, si vous désactivez la résolution des publicités différées, TVSDK déclenche une seule erreur 1109 (une seule analyse).
