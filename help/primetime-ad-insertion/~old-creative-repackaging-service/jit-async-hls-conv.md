---
description: CRS fournit un module de reconditionnement juste à temps (JIT) et asynchrone ainsi qu’une conversion HLS vers HLS. Le résultat du reconditionnement est une version au format HLS de l’élément créatif publicitaire d’origine. CRS place la version formatée HLS sur le serveur CDN (Content Delivery Network) pour l’utiliser si nécessaire.
title: Principales utilisations des CRS
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Principales utilisations des CRS {#main-uses-of-crs}

CRS fournit un module de reconditionnement juste à temps (JIT) et asynchrone ainsi qu’une conversion HLS vers HLS. Le résultat du reconditionnement est une version au format HLS de l’élément créatif publicitaire d’origine. CRS place la version formatée HLS sur le serveur CDN (Content Delivery Network) pour l’utiliser si nécessaire.

Dans le reconditionnement JIT, l’insertion de publicités Adobe Primetime commence le processus de reconditionnement lorsqu’elle rencontre pour la première fois un créatif publicitaire non HLS. Cela entraîne généralement des occasions perdues d’exécuter la publicité pendant le processus de reconditionnement.

Dans un reconditionnement asynchrone, le contenu publicitaire est transcodé et stocké avant d’être nécessaire, ce qui peut éliminer ces opportunités perdues.

Lors de la conversion HLS vers HLS, CRS reformate un élément créatif HLS en blocs de taille appropriée afin d’assurer une lecture cohérente.

## Regroupement juste à temps {#section_1BA344F2300B49F291865A7461EDFEAE}

La séquence de reconditionnement JIT est la suivante :

1. Le serveur de manifeste récupère une publicité.
1. Si le format de publicité est HLS, le serveur de manifeste insère la publicité dans le flux de contenu.
1. Si le format n’est pas HLS (par exemple, MP4, FLV ou WebM), le serveur de manifeste recherche une version transcodée sur le serveur CDN. S’il en trouve un, il insère la publicité transcodée dans le flux de contenu.
1. Si le format n’est pas HLS et que le serveur CDN n’a pas de version transcodée, le serveur de manifeste transmet la publicité à CRS, qui transcode le contenu publicitaire et stocke le résultat sur le serveur CDN en vue d’une utilisation ultérieure.
1. Le serveur de manifeste renvoie le contenu sans la publicité.

## Réplication asynchrone {#section_ACDFB43FDA4B445CB9F2A107FEB4F2F7}

Vous pouvez utiliser l’API décrite dans la section [API de réparation](../~old-creative-repackaging-service/api-repackage.md) pour précoder un créatif non HLS afin de minimiser la perte d’impressions et d’optimiser la monétisation.

## Conversion HLS-vers-HLS {#section_877A0E7E8FAF4C2DB086A31C24D53435}

Pour éviter toute mise en mémoire tampon et tout retard, un client télécharge une vidéo en petits blocs. Si les tailles du bloc sont incohérentes, la lecture peut être saccadée. La conversion HLS/HLS garantit que les blocs de données sont tous de même durée (par exemple, 6 secondes).

>[!NOTE]
>
>CRS produit la version 3 HLS, quelle que soit la version HLS qu’il reçoit.