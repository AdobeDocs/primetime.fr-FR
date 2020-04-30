---
description: Les clients peuvent utiliser Adobe Access (AAXS) DRM avec leurs propres systèmes de gestion de clés de contenu (CKMS) dotés de la fonction de CEK externe.
seo-description: Les clients peuvent utiliser Adobe Access (AAXS) DRM avec leurs propres systèmes de gestion de clés de contenu (CKMS) dotés de la fonction de CEK externe.
seo-title: Présentation du CEK externe d’Adobe Access DRM
title: Présentation du CEK externe d’Adobe Access DRM
uuid: ea0bba63-7743-4216-863f-392500998eb6
translation-type: tm+mt
source-git-commit: 92e04cbb5e94f60c8d06e94b826ff9361c10ef97

---


# Présentation du CEK externe d’Adobe Access DRM {#adobe-access-drm-external-cek-overview}

Les clients peuvent utiliser Adobe Access (AAXS) DRM avec leurs propres systèmes de gestion de clés de contenu (CKMS) dotés de la fonction de CEK externe.

Par défaut, Adobe Access (AAXS) DRM élimine la nécessité de traiter directement les clés, les certificats et les métadonnées DRM pendant le processus de création de package de contenu. Le SDK Java AAXS génère automatiquement une clé de chiffrement de contenu aléatoire (CEK) pendant la durée de création du pack et l’utilise pour chiffrer le contenu. Ensuite, le SDK chiffre le CEK lui-même et l’insère dans les métadonnées du contenu. Au moment de la délivrance de la licence, le serveur AAXS n’a besoin que de sa clé privée de serveur de licences AAXS pour accéder au CEK à partir des métadonnées afin de générer une licence.
