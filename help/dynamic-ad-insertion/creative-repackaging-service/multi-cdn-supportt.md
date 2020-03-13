---
description: Multi-CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.
seo-description: Multi-CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.
seo-title: Prise en charge multi-CDN
title: Prise en charge multi-CDN
uuid: 2b6d71f0-61c8-486b-a35a-f7ef3a9519d2
translation-type: tm+mt
source-git-commit: 6863b63c7fa0068c3c5060fb946515c6cc5e3bff

---


# Prise en charge multi-CDN {#multi-cdn-support}

Multi-CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.

Par défaut, toutes les ressources transcodées sont hébergées sur le réseau de diffusion de contenu Akamai détenu par Adobe. Cependant, vous pouvez choisir zéro ou plusieurs emplacements CDN supplémentaires de votre propre emplacement où CRS hébergera la ressource transcodée. Dans ce cas, vos fichiers et contenu transcodés peuvent donc être diffusés à partir du même CDN.

Lorsque le serveur de manifeste effectue une recherche pour les requêtes transcodées, il utilise une URL d’amorçage qui contient un certain nombre de paramètres  de. Si vous avez configuré un  de  multi-CDN, l’URL d’amorçage doit également contenir le `ptcdn` paramètre. Le serveur de manifeste utilise ce paramètre pour identifier le serveur CDN à partir duquel obtenir la version transcodée de la publicité.

La prise en charge multi-CDN est également disponible pour les solutions Primetime suivantes :

1. TVSDK pour Android
1. TVSDK pour HLS de bureau
1. TVSDK pour iOS

## Activer la prise en charge CDN {#section_1BA344F2300B49F291865A7461EDFEAE}

Par défaut, CRS est désactivé pour tous les clients

Contactez votre gestionnaire de compte technique Adobe pour configurer votre compte CRS afin qu’il utilise d’autres réseaux de diffusion de contenu pour héberger les ressources publicitaires transcodées. Vous devrez fournir les informations suivantes dont le CRS a besoin pour télécharger les ressources publicitaires transcodées sur le réseau de diffusion de contenu.

1. URL CDN
1. Détails de l’authentification
1. Format d’URL de sortie

En outre, votre gestionnaire de compte technique Adobe vous attribuera un surnom pour ce CDN. Vous devez transmettre ce surnom en tant que valeur du `ptcdn` paramètre dans l’URL d’amorçage.

Vous pouvez configurer plusieurs CDN sur CRS via le support Adobe. Cependant, le CDN utilisé pour sélectionner les ressources publicitaires à assembler via le serveur de manifeste doit être celui transmis en tant que valeur du `ptcdn` paramètre dans l’URL d’amorçage.
