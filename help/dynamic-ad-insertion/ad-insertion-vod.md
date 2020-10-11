---
title: Utiliser l’Ad Insertion pour VOD
description: Utilisation de l’Ad Insertion pour VOD
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Utiliser l’Ad Insertion pour VOD {#ad-insertion-vod}

L’Ad Insertion Primetime prend en charge l’insertion de publicités dans plusieurs ressources VOD, en utilisant les formats VAST 3.0+ ou VMAP 1.0+ standard.

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [IAB VAST](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD (Publicités mappées sur un serveur) {#server-mapped-ads}

L’Ad Insertion Primetime prend en charge l’insertion de VOD avec des publicités insérées avant le début de la lecture à l’aide des informations de chronologies ad hoc définies dans un format VMAP.  Le suivi des annonces VMAP, telles que les balises breakStart/breakEnd, sera fourni avec le suivi [des](set-up-ad-tracking.md)publicités.

## Réexécution complète par Événement (VOD avec repères Ad Decisioning) {#full-event-replay}

L’Ad Insertion Primetime prend également en charge des ressources VOD spécialisées qui contiennent des indices dans le flux de contenu lui-même, tels que ceux détectés lors de la lecture de événements en direct précédemment enregistrés. Pour plus d’informations sur les types de indices de décision (ou formats de indices) que nous prenons en charge, voir [Utilisation de l’Ad Insertion en direct/linéaire](ad-insertion-live-linear-stream.md).

Nous prenons en charge à la fois les scénarios de demande d’annonce unique et de demande d’annonce multiple en parallèle pour les ressources VOD contenant plusieurs coupures d’annonce. Pour plus d’informations, voir `ptmulticall` paramètre dans la description [du](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)paramètre. Les formats VAST et VMAP sont pris en charge pour les indices en flux continu.
