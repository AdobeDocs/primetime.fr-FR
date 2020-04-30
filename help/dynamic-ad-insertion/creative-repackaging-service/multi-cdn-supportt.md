---
description: Multi CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.
seo-description: Multi CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.
seo-title: Prise en charge de CDN multiple
title: Prise en charge de CDN multiple
uuid: 2b6d71f0-61c8-486b-a35a-f7ef3a9519d2
translation-type: tm+mt
source-git-commit: 6863b63c7fa0068c3c5060fb946515c6cc5e3bff

---


# Prise en charge de CDN multiple {#multi-cdn-support}

Multi CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.

Par défaut, toutes les ressources transcodées sont hébergées sur le réseau de diffusion de contenu Akamai détenu par Adobe. Cependant, vous pouvez choisir zéro ou plusieurs emplacements CDN supplémentaires dans lesquels CRS hébergera la ressource transcodée. Ainsi, dans ce cas, vos ressources et contenu transcodés peuvent être diffusés à partir du même CDN.

Lorsque le serveur de manifeste effectue une recherche pour les requêtes transcodées, il utilise une URL d’amorçage qui contient plusieurs paramètres de requête. Si vous avez configuré un environnement CDN multiple, l&#39;URL d&#39;amorçage doit également contenir le `ptcdn` paramètre. Le serveur de manifeste utilise ce paramètre pour identifier le serveur CDN à partir duquel obtenir la version transcodée de la publicité.

La prise en charge de plusieurs CDN est également disponible pour les solutions Primetime suivantes :

1. TVSDK pour Android
1. TVSDK pour HLS de bureau
1. TVSDK pour iOS

## Activation de la prise en charge CDN {#section_1BA344F2300B49F291865A7461EDFEAE}

Par défaut, CRS est désactivé pour tous les clients.

Contactez votre gestionnaire de compte technique Adobe pour configurer votre compte CRS afin d’utiliser d’autres réseaux de diffusion de contenu pour héberger les ressources publicitaires transcodées. Vous devrez fournir les informations suivantes dont CRS a besoin pour télécharger les ressources publicitaires transcodées sur le réseau de diffusion de contenu.

1. URL CDN
1. Détails de l’authentification
1. Format d’URL de sortie

En outre, votre gestionnaire de compte technique Adobe vous fournira un surnom pour ce CDN. Vous devez transmettre ce nom en tant que valeur du `ptcdn` paramètre dans l’URL d’amorçage.

Vous pouvez configurer plusieurs CDN sur CRS via l’assistance Adobe. Cependant, le réseau de diffusion de contenu utilisé pour sélectionner les ressources publicitaires à assembler via le serveur de manifeste doit être celui qui est transmis en tant que valeur du `ptcdn` paramètre dans l’URL d’amorçage.
