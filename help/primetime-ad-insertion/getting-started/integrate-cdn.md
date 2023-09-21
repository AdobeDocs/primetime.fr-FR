---
title: Intégrer votre réseau de diffusion de contenu
description: Intégration de votre réseau de diffusion de contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Intégrer votre réseau de diffusion de contenu {#integrating-cdn}

L’Ad Insertion Primetime sert de proxy entre votre application cliente et manifeste, et non les blocs vidéo eux-mêmes. Déployez votre contenu sur le réseau de diffusion de contenu de votre choix et transmettez l’URL à l’Ad Insertion Primetime à l’aide de l’API du Bootstrap. Pour plus d’informations sur l’intégration, voir [Réseau de diffusion de contenu pris en charge](/help/primetime-ad-insertion/technical-reference/supported-cdns.md).

## Modèles de segmentation en jetons CDN pris en charge {#cdn-tokenization-schemes}

Les CDN ont souvent différents schémas de segmentation en unités pour l’autorisation des fragments. Ad Insertion Primetime prend en charge de manière native les principaux réseaux CDN, notamment :

* Akamai
* Limelight
* Centurylink/Level3
* Contactez votre représentant de l’assistance Primetime pour obtenir la liste complète des CDN pris en charge.

Pour plus d’informations sur la variable `pttoken` paramètre, voir [Description des paramètres de l’API Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md#parameter-description).

## Configuration des publicités à diffuser à partir du réseau de diffusion de contenu {#configure-ad-deliver-from-cdn}

Vous pouvez diffuser des publicités et du contenu à partir du même réseau de diffusion de contenu afin de maintenir l’affinité du contenu, de contourner le blocage des publicités et/ou d’optimiser le nombre de connexions requises à partir de l’application cliente. Primetime Ad Insertion prend en charge les règles de réécriture de fragments pour mapper des fragments à votre réseau de diffusion de contenu. Pour plus d’informations, voir [Réécriture du manifeste](/help/primetime-ad-insertion/technical-reference/manifest-rewriting.md).

## Amélioration des performances de démarrage avec votre réseau de diffusion de contenu {#increase-startup-performance}

Pour plus d’informations, voir [Optimisation du démarrage](/help/primetime-ad-insertion/best-practices/optimize-video-startup-time.md).

## Fonctionnalités multi-CDN {#enable-multi-cdn-fetures}

Contactez votre représentant du support Primetime pour activer les fonctionnalités multi-CDN.
