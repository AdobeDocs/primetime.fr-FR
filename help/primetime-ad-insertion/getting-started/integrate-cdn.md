---
title: Intégration de votre CDN
description: Intégration de votre CDN
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Intégrer votre CDN {#integrating-cdn}

L’Ad Insertion Primetime sert de proxy entre votre application cliente et les manifestes, et non les découpages vidéo eux-mêmes. Déployez votre contenu sur le CDN de votre choix et transmettez l’URL à l’Ad Insertion Primetime à l’aide de l’API du Bootstrap. Pour plus d’informations sur l’intégration, voir [CDN pris en charge](/help/primetime-ad-insertion/technical-reference/supported-cdns.md).

## Schémas de segmentation en jetons CDN pris en charge {#cdn-tokenization-schemes}

Les réseaux CDN ont souvent différents schémas de segmentation pour l’autorisation de fragments. L’Ad Insertion Primetime prend en charge nativement les principaux réseaux CDN, notamment :

* Akamai
* Limelight
* Centurylink / Level3
* Contactez votre représentant d’assistance Primetime pour obtenir une liste complète des réseaux de diffusion de contenu pris en charge.

Pour plus d&#39;informations sur le paramètre `pttoken`, voir [description du paramètre de l&#39;API du Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md#parameter-description).

## Configurez les publicités à diffuser à partir du contenu CDN {#configure-ad-deliver-from-cdn}

Vous pouvez diffuser des publicités et du contenu à partir du même réseau de diffusion de contenu afin de conserver l’affinité du contenu, de contourner le blocage des publicités et/ou d’optimiser le nombre de connexions requises à partir de l’application cliente. L’Ad Insertion Primetime prend en charge les règles de réécriture de fragments afin de mapper les fragments à votre CDN de contenu. Pour plus d’informations, voir [Réécriture du manifeste](/help/primetime-ad-insertion/technical-reference/manifest-rewriting.md).

## Augmentez les performances de début avec votre réseau de diffusion de contenu {#increase-startup-performance}

Pour plus d’informations, voir [Optimisation du début-up](/help/primetime-ad-insertion/best-practices/optimize-video-startup-time.md).

## Fonctionnalités multiCDN {#enable-multi-cdn-fetures}

Contactez votre représentant du support technique Primetime pour activer les fonctionnalités multi-CDN.
