---
description: Les clients peuvent utiliser la gestion des droits numériques AAXS (Adobe Access) avec leurs propres systèmes de gestion de clés de contenu (CKMS) avec la fonction CEK externe.
seo-description: Les clients peuvent utiliser la gestion des droits numériques AAXS (Adobe Access) avec leurs propres systèmes de gestion de clés de contenu (CKMS) avec la fonction CEK externe.
seo-title: Aperçu du CEK externe DRM d'accès Adobe
title: Aperçu du CEK externe DRM d'accès Adobe
uuid: ea0bba63-7743-4216-863f-392500998eb6
translation-type: tm+mt
source-git-commit: 92e04cbb5e94f60c8d06e94b826ff9361c10ef97
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Aperçu du CEK externe DRM d&#39;accès aux Adobes {#adobe-access-drm-external-cek-overview}

Les clients peuvent utiliser la gestion des droits numériques AAXS (Adobe Access) avec leurs propres systèmes de gestion de clés de contenu (CKMS) avec la fonction CEK externe.

Par défaut, la gestion des droits d’accès aux Adobes (AAXS) DRM élimine la nécessité de traiter directement les clés, les certificats et les métadonnées DRM pendant le processus de création de package de contenu. Le SDK Java AAXS génère automatiquement une clé de chiffrement de contenu aléatoire (CEK) pendant la durée de création du pack et l’utilise pour chiffrer le contenu. Ensuite, le SDK chiffre le CEK lui-même et l’insère dans les métadonnées du contenu. Au moment de la délivrance de la licence, le serveur AAXS n’a besoin que de sa clé privée de serveur de licences AAXS pour accéder au CEK à partir des métadonnées afin de générer une licence.
