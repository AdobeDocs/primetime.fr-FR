---
description: CRS fournit un reconditionnement juste à temps (JIT) et asynchrone et une conversion HLS-to-HLS. Le résultat du reconditionnement est une version au format HLS du créatif publicitaire d’origine. CRS place la version au format HLS sur le serveur CDN (Content Network) pour l’utiliser au besoin.
seo-description: CRS fournit un reconditionnement juste à temps (JIT) et asynchrone et une conversion HLS-to-HLS. Le résultat du reconditionnement est une version au format HLS du créatif publicitaire d’origine. CRS place la version au format HLS sur le serveur CDN (Content Network) pour l’utiliser au besoin.
seo-title: Principales utilisations des SIR
title: Principales utilisations des SIR
uuid: df2caa67-bc94-4146-9b93-14edc060c3d5
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Principales utilisations des SIR {#main-uses-of-crs}

CRS fournit un reconditionnement juste à temps (JIT) et asynchrone et une conversion HLS-to-HLS. Le résultat du reconditionnement est une version au format HLS du créatif publicitaire d’origine. CRS place la version au format HLS sur le serveur CDN (Content Network) pour l’utiliser au besoin.

Dans JIT, le reconditionnement d’Adobe Primetime et l’insertion de publicités commence le processus de reconditionnement lorsqu’il rencontre pour la première fois un élément créatif publicitaire non-HLS. Cela entraîne généralement une perte d’opportunités d’exécution de la publicité pendant le processus de reconditionnement.

Dans un reconditionnement asynchrone, le créatif publicitaire est transcodé et stocké avant d’être nécessaire, ce qui peut éliminer les opportunités perdues.

Lors de la conversion HLS-to-HLS, CRS reformate un élément créatif HLS en blocs de taille appropriée afin d’assurer une lecture cohérente.

## Rackage juste à temps {#section_1BA344F2300B49F291865A7461EDFEAE}

La séquence pour le reconditionnement JIT est la suivante :

1. Le serveur de manifeste récupère une publicité.
1. Si le format de la publicité est HLS, le serveur de manifeste insère la publicité dans le flux de contenu.
1. Si le format n’est pas HLS (par exemple, MP4, FLV ou WebM), le serveur de manifeste recherche une version transcodée sur le serveur CDN. S’il en trouve un, il insère la publicité transcodée dans le flux de contenu.
1. Si le format n’est pas HLS et que le serveur CDN n’a pas de version transcodée, le serveur de manifeste transmet la publicité à CRS, qui transcode le créatif de la publicité et stocke le résultat sur le serveur CDN pour une utilisation ultérieure.
1. Le serveur de manifeste renvoie le contenu sans la publicité.

## Réemballage asynchrone {#section_ACDFB43FDA4B445CB9F2A107FEB4F2F7}

Vous pouvez utiliser l’API décrite dans l’API [de](../creative-repackaging-service/api-repackage.md) reconditionnement pour précoder un élément créatif non-HLS afin de minimiser les pertes d’impressions et d’optimiser la monétisation.

## Conversion HLS vers HLS {#section_877A0E7E8FAF4C2DB086A31C24D53435}

Pour éviter la mise en mémoire tampon et les retards, un client télécharge une vidéo en petits morceaux. Si les tailles des blocs sont incohérentes, la lecture peut être saccadée. La conversion HLS/HLS garantit que les blocs de données sont tous de la même durée (par exemple, 6 secondes).

>[!NOTE]
>
>CRS produit HLS version 3, quelle que soit la version HLS qu’il reçoit.