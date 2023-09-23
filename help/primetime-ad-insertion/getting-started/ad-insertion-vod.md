---
title: Utilisez Ad Insertion pour VOD
description: Utilisation d’Ad Insertion pour VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Utilisez Ad Insertion pour VOD {#ad-insertion-vod}

L’Ad Insertion Primetime prend en charge l’insertion d’annonces dans plusieurs ressources VOD, à l’aide des formats VAST 3.0+ ou VMAP 1.0+ standard.

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [VAST IAB](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD (mappages publicitaires) {#server-mapped-ads}

Primetime Ad Insertion prend en charge l’insertion VOD avec publicités insérées avant le début de la lecture à l’aide des informations de chronologies publicitaires définies dans un format VMAP.  Le suivi des publicités spécifique à VMAP, tel que les balises breakStart/breakEnd, est fourni avec [Suivi des publicités](set-up-ad-tracking.md).

## Relecture d’événement complet (VOD avec repères Ad Decisioning) {#full-event-replay}

L’Ad Insertion Primetime prend également en charge les ressources VOD spécialisées qui contiennent des indices dans le flux de contenu lui-même, comme détecté dans la lecture d’événements en direct précédemment enregistrés. Pour plus d’informations sur les types de repères de décision publicitaires (ou formats de repère) pris en charge, voir [Utilisation de l’Ad Insertion en direct/linéaire](ad-insertion-live-linear-stream.md).

Nous prenons en charge à la fois les scénarios de demande d’annonce unique et de demande d’annonce multiple parallèles pour les ressources VOD contenant plusieurs coupures publicitaires. Pour plus d’informations, voir `ptmulticall` du paramètre [Description des paramètres](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md). Les formats VAST et VMAP sont pris en charge pour les indices en flux continu.
