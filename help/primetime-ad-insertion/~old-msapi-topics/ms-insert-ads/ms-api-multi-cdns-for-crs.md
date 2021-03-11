---
description: Bien que le scénario par défaut du service de reconditionnement créatif (CRS) consiste à utiliser un réseau CDN (Content Diffusion Network), vous pouvez déployer des ressources CRS sur plusieurs réseaux CDN.
title: Prise en charge de plusieurs réseaux CDN pour CRS et diffusion
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Prise en charge de plusieurs CDN pour CRS et diffusion {#multiple-cdn-support-for-crs-ad-delivery}

Bien que le scénario par défaut du service de reconditionnement créatif (CRS) consiste à utiliser un réseau CDN (Content Diffusion Network), vous pouvez déployer des ressources CRS sur plusieurs réseaux CDN.

## Conditions requises

Vous pouvez utiliser plusieurs CDN pour les raisons suivantes :

* Configuration requise pour une évolutivité pour les événements de visualisation volumineux
* Obligation de faire correspondre la source CDN du fichier CRS à la source CDN du contenu principal.
* Obligation d’utiliser un CDN différent de celui du CDN par défaut (Akamai) du CRS.

Lorsque le serveur de manifeste effectue une recherche pour les requêtes transcodées, il utilise une URL d’amorçage qui contient plusieurs paramètres de requête. Si vous avez configuré un environnement CDN multiple, l’URL d’amorçage doit également contenir le paramètre `ptcdn`. Le serveur de manifeste utilise ce paramètre pour identifier le serveur CDN à partir duquel obtenir la version transcodée de la publicité.

Pour plus de détails, voir [Prise en charge de plusieurs CDN](../../~old-creative-repackaging-service/multi-cdn-supportt.md) dans la documentation CRS.
