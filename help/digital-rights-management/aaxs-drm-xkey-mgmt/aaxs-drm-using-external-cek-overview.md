---
description: Les clients peuvent utiliser Adobe Access (AAXS) DRM avec leurs propres systèmes de gestion de clés de contenu (CKMS) avec la fonctionnalité de CEK externe.
title: Présentation du CEK externe Adobe Access DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Présentation du CEK externe Adobe Access DRM {#adobe-access-drm-external-cek-overview}

Les clients peuvent utiliser Adobe Access (AAXS) DRM avec leurs propres systèmes de gestion de clés de contenu (CKMS) avec la fonctionnalité de CEK externe.

Par défaut, Adobe Access (AAXS) DRM élimine la nécessité de gérer directement les clés, les certificats et les métadonnées DRM pendant le processus de conditionnement du contenu. Le SDK Java AXS génère automatiquement une clé de chiffrement de contenu (CEK) aléatoire au moment du conditionnement et l’utilise pour chiffrer le contenu. Ensuite, le SDK chiffre le CEK lui-même et l’insère dans les métadonnées du contenu. Au moment de l’émission de la licence, le serveur AXS n’a besoin que de sa clé privée de serveur de licences AAXS pour accéder au CEK à partir des métadonnées afin de générer une licence.
