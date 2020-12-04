---
description: CRS fournit des solutions de reconditionnement juste à temps et asynchrones et de conversion HLS en HLS. Le résultat du reconditionnement est une version au format HLS de l’élément créatif publicitaire d’origine. CRS place la version au format HLS sur le serveur CDN (Content diffusion Network) pour l’utiliser si nécessaire.
seo-description: CRS fournit des solutions de reconditionnement juste à temps et asynchrones et de conversion HLS en HLS. Le résultat du reconditionnement est une version au format HLS de l’élément créatif publicitaire d’origine. CRS place la version au format HLS sur le serveur CDN (Content diffusion Network) pour l’utiliser si nécessaire.
seo-title: Principales utilisations des SIR
title: Principales utilisations des SIR
uuid: df2caa67-bc94-4146-9b93-14edc060c3d5
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Principales utilisations des SIR {#main-uses-of-crs}

CRS fournit des solutions de reconditionnement juste à temps et asynchrones et de conversion HLS en HLS. Le résultat du reconditionnement est une version au format HLS de l’élément créatif publicitaire d’origine. CRS place la version au format HLS sur le serveur CDN (Content diffusion Network) pour l’utiliser si nécessaire.

Dans JIT, le reconditionnement d’Adobe Primetime et l’insertion d’une annonce commence le processus de reconditionnement lorsqu’elle rencontre pour la première fois un élément créatif publicitaire non HLS. Cela entraîne généralement la perte d’opportunités d’exécution de la publicité pendant le processus de reconditionnement.

Lors d’un reconditionnement asynchrone, la création publicitaire est transcodée et stockée avant d’être utilisée, ce qui peut éliminer les opportunités perdues.

Lors de la conversion HLS/HLS, CRS reformate un fichier HLS et un fichier créatif en blocs de taille appropriée afin d’assurer une lecture cohérente.

## Restauration juste à temps {#section_1BA344F2300B49F291865A7461EDFEAE}

La séquence pour le reconditionnement JIT est la suivante :

1. Le serveur de manifeste récupère une publicité.
1. Si le format de la publicité est HLS, le serveur de manifeste insère la publicité dans le flux de contenu.
1. Si le format n’est pas HLS (par exemple, MP4, FLV ou WebM), le serveur de manifeste recherche une version transcodée sur le serveur CDN. S’il en trouve un, il insère la publicité transcodée dans le flux de contenu.
1. Si le format n’est pas HLS et que le serveur CDN n’a pas de version transcodée, le serveur de manifeste transmet la publicité à CRS, qui transcode la création publicitaire et stocke le résultat sur le serveur CDN pour une utilisation ultérieure.
1. Le serveur de manifeste renvoie le contenu sans la publicité.

## Réparation asynchrone {#section_ACDFB43FDA4B445CB9F2A107FEB4F2F7}

Vous pouvez utiliser l&#39;API décrite dans [API de retraitement](../creative-repackaging-service/api-repackage.md) pour prétranscoder un élément créatif non HLS afin de minimiser la perte d&#39;impressions et d&#39;optimiser la monétisation.

## Conversion HLS-en-HLS {#section_877A0E7E8FAF4C2DB086A31C24D53435}

Pour éviter la mise en mémoire tampon et les retards, un client télécharge une vidéo en petits morceaux. Si les tailles des blocs sont incohérentes, la lecture peut être risquée. La conversion HLS/HLS garantit que les blocs de données sont tous de la même durée (par exemple, 6 secondes).

>[!NOTE]
>
>CRS produit HLS version 3, quelle que soit la version HLS reçue.