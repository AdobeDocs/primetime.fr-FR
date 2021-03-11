---
description: Lorsque TVSDK rencontre un VMAP endommagé dans une réponse du serveur d’annonces, il envoie une erreur 1109 (NETWORK_AD_URL_FAILED).
keywords: 1109;NETWORK_AD_URL_FAILED;VMAP endommagée
title: Gestion des erreurs du client pour le VMAP endommagé
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Gestion des erreurs du client pour le VMAP endommagé {#client-error-handling-for-broken-vmap}

Lorsque TVSDK rencontre un VMAP endommagé dans une réponse du serveur d’annonces, il envoie une erreur 1109 (NETWORK_AD_URL_FAILED).

En fonction de la nature de la réponse du serveur d’annonces et des paramètres de chargement des annonces, votre lecteur peut recevoir différents nombres d’erreurs 1109 lorsque TVSDK rencontre un VMAP endommagé dans une réponse du serveur d’annonces.

Examinons un scénario dans lequel la réponse du serveur d’annonces pointe vers le fichier XML VMAP. Supposons également que la réponse du serveur d’annonces comporte quatre emplacements d’annonces disponibles, chacun pointant vers le même VMAP. Enfin, disons que ce VMAP est cassé.

Dans ce scénario, si la résolution des publicités paresseuses est activée ( [Activer la résolution des publicités paresseuses](../../../tvsdk-2.7-for-android/ad-insertion/c-psdk-android-2.7-lazy-ad-resolving/t-psdk-android-2.7-enable-lazy-ad-resolving.md)), TVSDK enverra deux erreurs 1109 (et non une erreur comme prévu) : une erreur est envoyée sur chaque passe d’analyse sur la chronologie. En effet, lorsque la résolution différée des publicités est activée, TVSDK analyse les publicités en 2 passes : la première passe se produit juste avant les débuts de lecture du contenu pour les publicités preroll, et la seconde passe après les débuts de lecture, pour les publicités mid-roll et post-roll.

>[!NOTE]
>
>Dans ce scénario, si vous désactivez la résolution des publicités paresseuses, TVSDK déclenche uniquement une erreur 1109 (une seule passe d’analyse).

