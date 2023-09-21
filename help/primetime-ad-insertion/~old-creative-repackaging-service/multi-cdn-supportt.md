---
description: Le réseau de diffusion de contenu multiple permet de définir un ou plusieurs emplacements de réseau de diffusion de contenu pour diffuser des publicités transcodées.
title: Prise en charge multi-CDN
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Prise en charge multi-CDN {#multi-cdn-support}

Le réseau de diffusion de contenu multiple permet de définir un ou plusieurs emplacements de réseau de diffusion de contenu pour diffuser des publicités transcodées.

Par défaut, toutes les ressources transcodées sont hébergées sur le réseau de diffusion de contenu Akamai détenu par l’Adobe. Cependant, vous pouvez choisir aucun ou plusieurs emplacements CDN supplémentaires où CRS hébergera la ressource transcodée. Ainsi, dans ce cas, vos ressources et contenu transcodés peuvent être diffusés à partir du même CDN.

Lorsque le serveur de manifeste effectue une recherche pour les requêtes transcodées, il utilise une URL de bootstrap contenant un certain nombre de paramètres de requête. Si vous avez configuré un environnement multi-CDN, l’URL d’amorçage doit également contenir la variable `ptcdn` parameter.Le serveur manifest utilise ce paramètre pour identifier le serveur CDN à partir duquel obtenir la version transcodée de la publicité.

La prise en charge multi-CDN est également disponible pour les solutions Primetime suivantes :

1. TVSDK pour Android
1. TVSDK pour Desktop HLS
1. TVSDK pour iOS

## Activation de la prise en charge du réseau CDN {#section_1BA344F2300B49F291865A7461EDFEAE}

Par défaut, CRS est désactivé pour tous les clients.

Contactez votre gestionnaire de compte technique d’Adobe pour configurer votre compte CRS afin d’utiliser d’autres CDN pour héberger les ressources de publicité transcodées. Vous devrez fournir les informations suivantes dont CRS a besoin pour télécharger les ressources de publicité transcodées sur le CDN.

1. URL CDN
1. Détails de l’authentification
1. Format d’URL de sortie

En outre, votre gestionnaire de compte technique Adobe vous donnera un surnom pour ce réseau de diffusion de contenu. Vous devez le transmettre comme la valeur de la variable `ptcdn` dans l’URL du Bootstrap.

Vous pouvez configurer plusieurs CDN sur la fin CRS via la prise en charge des Adobes. Cependant, le réseau de diffusion de contenu utilisé pour sélectionner des ressources publicitaires à assembler via le serveur manifeste doit être celui qui est transmis comme valeur de `ptcdn` dans l’URL du Bootstrap.
