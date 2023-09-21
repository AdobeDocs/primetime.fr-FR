---
description: Bien que le scénario de service de reconditionnement de création (CRS) par défaut consiste à utiliser un réseau de diffusion de contenu (CDN), vous pouvez déployer des ressources CRS sur plusieurs réseaux de diffusion de contenu.
title: Prise en charge de plusieurs CDN pour CRS et diffusion
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Prise en charge de plusieurs CDN pour CRS et diffusion {#multiple-cdn-support-for-crs-ad-delivery}

Bien que le scénario de service de reconditionnement de création (CRS) par défaut consiste à utiliser un réseau de diffusion de contenu (CDN), vous pouvez déployer des ressources CRS sur plusieurs réseaux de diffusion de contenu.

## Conditions

Vous pouvez utiliser plusieurs CDN pour les raisons suivantes :

* Configuration requise pour une mise à l’échelle pour les événements de visionnage de grande taille
* Une exigence pour faire correspondre la source CDN de la ressource CRS à la source CDN du contenu principal.
* Obligation d’utiliser un autre réseau de diffusion de contenu que le réseau CDN par défaut par défaut (Akamai).

Lorsque le serveur de manifeste effectue une recherche pour les requêtes transcodées, il utilise une URL de bootstrap contenant un certain nombre de paramètres de requête. Si vous avez configuré un environnement multi-CDN, l’URL d’amorçage doit également contenir la variable `ptcdn` . Le serveur manifest utilise ce paramètre pour identifier le serveur CDN à partir duquel obtenir la version transcodée de la publicité.

Pour plus d’informations, voir [Prise en charge multi-CDN](../../~old-creative-repackaging-service/multi-cdn-supportt.md) dans la documentation CRS.
