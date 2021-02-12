---
description: Multi CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.
seo-description: Multi CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.
seo-title: Prise en charge de CDN multiple
title: Prise en charge de CDN multiple
uuid: 2b6d71f0-61c8-486b-a35a-f7ef3a9519d2
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# Prise en charge de plusieurs CDN {#multi-cdn-support}

Multi CDN permet de définir un ou plusieurs emplacements CDN pour diffuser des publicités transcodées.

Par défaut, toutes les ressources transcodées sont hébergées sur le réseau de diffusion de contenu Akamai détenu par l’Adobe. Cependant, vous pouvez choisir zéro ou plusieurs emplacements CDN supplémentaires dans lesquels CRS hébergera la ressource transcodée. Ainsi, dans ce cas, vos ressources et contenu transcodés peuvent être diffusés à partir du même CDN.

Lorsque le serveur de manifeste effectue une recherche pour les requêtes transcodées, il utilise une URL d’amorçage qui contient plusieurs paramètres de requête. Si vous avez configuré un environnement CDN multiple, l’URL d’amorçage devra également contenir le paramètre `ptcdn`. Le serveur de manifeste utilise ce paramètre pour identifier le serveur CDN à partir duquel obtenir la version transcodée de la publicité.

La prise en charge de plusieurs CDN est également disponible pour les solutions Primetime suivantes :

1. TVSDK pour Android
1. TVSDK pour HLS de bureau
1. TVSDK pour iOS

## Activer la prise en charge CDN {#section_1BA344F2300B49F291865A7461EDFEAE}

Par défaut, CRS est désactivé pour tous les clients.

Contactez votre gestionnaire de compte technique Adobe pour configurer votre compte CRS afin d’utiliser d’autres réseaux de diffusion de contenu pour héberger les ressources publicitaires transcodées. Vous devrez fournir les informations suivantes dont CRS a besoin pour télécharger les ressources publicitaires transcodées sur le réseau de diffusion de contenu.

1. URL CDN
1. Détails de l’authentification
1. Format d’URL de sortie

En outre, votre gestionnaire de compte technique Adobe vous donnera un surnom pour ce CDN. Vous devez transmettre ce surnom en tant que valeur du paramètre `ptcdn` dans l’URL du Bootstrap.

Vous pouvez configurer plusieurs CDN sur la fin CRS via le support Adobe. Cependant, le CDN utilisé pour sélectionner les ressources publicitaires à assembler via le serveur de manifeste doit être celui qui est transmis en tant que valeur du paramètre `ptcdn` dans l’URL du Bootstrap.
