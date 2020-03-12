---
description: Les clients peuvent utiliser Adobe Access (AAXS) DRM avec leurs propres systèmes de gestion des clés de contenu (CKMS) avec la fonction de CEK externe.
seo-description: Les clients peuvent utiliser Adobe Access (AAXS) DRM avec leurs propres systèmes de gestion des clés de contenu (CKMS) avec la fonction de CEK externe.
seo-title: Présentation du CEK externe DRM d’Adobe Access
title: Présentation du CEK externe DRM d’Adobe Access
uuid: ea0bba63-7743-4216-863f-392500998eb6
translation-type: tm+mt
source-git-commit: 92e04cbb5e94f60c8d06e94b826ff9361c10ef97

---


# Présentation du CEK externe DRM d’Adobe Access {#adobe-access-drm-external-cek-overview}

Les clients peuvent utiliser Adobe Access (AAXS) DRM avec leurs propres systèmes de gestion des clés de contenu (CKMS) avec la fonction de CEK externe.

Par défaut, le DRM d’Adobe Access (AAXS) élimine la nécessité de gérer directement les clés, les certificats et les métadonnées DRM pendant le processus de création de package de contenu. Le SDK Java AAXS génère automatiquement une clé de chiffrement de contenu aléatoire (CEK) au cours de l’assemblage et l’utilise pour chiffrer le contenu. Ensuite, le SDK chiffre le CEK lui-même et l’insère dans les métadonnées du contenu. Au moment de la délivrance de la licence, le serveur AAXS n’a besoin que de sa clé privée de serveur de licences AAXS pour accéder au CEK à partir des métadonnées afin de générer une licence.
