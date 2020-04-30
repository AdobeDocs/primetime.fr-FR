---
description: Bien que le scénario par défaut du service de reconditionnement créatif (CRS) consiste à utiliser un réseau CDN (Content Diffusion Network), vous pouvez déployer des ressources CRS sur plusieurs réseaux CDN.
seo-description: Bien que le scénario par défaut du service de reconditionnement créatif (CRS) consiste à utiliser un réseau CDN (Content Diffusion Network), vous pouvez déployer des ressources CRS sur plusieurs réseaux CDN.
seo-title: Prise en charge de plusieurs réseaux CDN pour CRS et diffusion
title: Prise en charge de plusieurs réseaux CDN pour CRS et diffusion
uuid: c5557a38-aa49-4161-bb58-3e8dff9a4d64
translation-type: tm+mt
source-git-commit: f327b45de7e482dcb25407659846b2098f1fd49d

---


# Prise en charge de plusieurs réseaux CDN pour CRS et diffusion {#multiple-cdn-support-for-crs-ad-delivery}

Bien que le scénario par défaut du service de reconditionnement créatif (CRS) consiste à utiliser un réseau CDN (Content Diffusion Network), vous pouvez déployer des ressources CRS sur plusieurs réseaux CDN.

## Conditions requises

Vous pouvez utiliser plusieurs CDN pour les raisons suivantes :

* Configuration requise pour une évolutivité pour les événements de visualisation volumineux
* Obligation de faire correspondre la source CDN du fichier CRS à la source CDN du contenu principal.
* Obligation d’utiliser un CDN différent de celui du CDN par défaut (Akamai) du CRS.

Lorsque le serveur de manifeste effectue une recherche pour les requêtes transcodées, il utilise une URL d’amorçage qui contient plusieurs paramètres de requête. Si vous avez configuré un environnement multi-CDN, l’URL d’amorçage doit également contenir le `ptcdn` paramètre. Le serveur de manifeste utilise ce paramètre pour identifier le serveur CDN à partir duquel obtenir la version transcodée de la publicité.

Pour plus d’informations, voir Prise en charge [de](../../creative-repackaging-service/multi-cdn-supportt.md) plusieurs CDN dans la documentation CRS.
