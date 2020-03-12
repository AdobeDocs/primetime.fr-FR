---
description: Bien que le scénario CRS (Creative Repackage Service) par défaut consiste à utiliser un réseau CDN (Content Network), vous pouvez déployer des ressources CRS sur plusieurs CDN.
seo-description: Bien que le scénario CRS (Creative Repackage Service) par défaut consiste à utiliser un réseau CDN (Content Network), vous pouvez déployer des ressources CRS sur plusieurs CDN.
seo-title: Prise en charge de CDN multiples pour CRS et les  de
title: Prise en charge de CDN multiples pour CRS et les  de
uuid: c5557a38-aa49-4161-bb58-3e8dff9a4d64
translation-type: tm+mt
source-git-commit: f327b45de7e482dcb25407659846b2098f1fd49d

---


# Prise en charge de CDN multiples pour CRS et les  de {#multiple-cdn-support-for-crs-ad-delivery}

Bien que le scénario CRS (Creative Repackage Service) par défaut consiste à utiliser un réseau CDN (Content Network), vous pouvez déployer des ressources CRS sur plusieurs CDN.

## Conditions requises

Vous pouvez utiliser plusieurs CDN pour les raisons suivantes :

* Configuration requise pour une évolutivité pour les d’affichage volumineux 
* Obligation de faire correspondre la source CDN du fichier CRS à la source CDN du contenu principal.
* Obligation d’utiliser un CDN différent du CDN par défaut (Akamai) CRS.

Lorsque le serveur de manifeste effectue une recherche pour les requêtes transcodées, il utilise une URL d’amorçage qui contient un certain nombre de paramètres  de. Si vous avez configuré un  de  multi-CDN, l’URL d’amorçage devra également contenir le `ptcdn` paramètre. Le serveur de manifeste utilise ce paramètre pour identifier le serveur CDN à partir duquel obtenir la version transcodée de la publicité.

Pour plus d’informations, voir Prise en charge [](../../creative-repackaging-service/multi-cdn-supportt.md) multi-CDN dans la documentation CRS.
