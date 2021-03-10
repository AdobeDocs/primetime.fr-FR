---
description: Les clients peuvent utiliser la gestion des droits numériques AAXS (Adobe Access) avec leurs propres systèmes de gestion de clés de contenu (CKMS) avec la fonction CEK externe.
title: Aperçu du CEK externe DRM d'accès Adobe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# Aperçu du CEK externe DRM d&#39;accès aux Adobes {#adobe-access-drm-external-cek-overview}

Les clients peuvent utiliser la gestion des droits numériques AAXS (Adobe Access) avec leurs propres systèmes de gestion de clés de contenu (CKMS) avec la fonction CEK externe.

Par défaut, la gestion des droits d’accès aux Adobes (AAXS) DRM élimine la nécessité de traiter directement les clés, les certificats et les métadonnées DRM pendant le processus de création de package de contenu. Le SDK Java AAXS génère automatiquement une clé de chiffrement de contenu aléatoire (CEK) pendant la durée de création du pack et l’utilise pour chiffrer le contenu. Ensuite, le SDK chiffre le CEK lui-même et l’insère dans les métadonnées du contenu. Au moment de la délivrance de la licence, le serveur AAXS n’a besoin que de sa clé privée de serveur de licences AAXS pour accéder au CEK à partir des métadonnées afin de générer une licence.
