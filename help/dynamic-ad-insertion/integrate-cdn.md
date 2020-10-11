---
title: Intégration de votre CDN
description: Intégration de votre CDN
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# Intégration de votre CDN {#integrating-cdn}

L’Ad Insertion Primetime sert de proxy entre votre application cliente et les manifestes, et non les découpages vidéo eux-mêmes. Déployez votre contenu sur le CDN de votre choix et transmettez l’URL à l’Ad Insertion Primetime à l’aide de l’API du Bootstrap.<!-- For integration details, see [Supported CDNs](supported-cdns.md).-->

## Systèmes de segmentation en jetons CDN pris en charge {#cdn-tokenization-schemes}

Les réseaux CDN ont souvent différents schémas de segmentation pour l’autorisation de fragments. L’Ad Insertion Primetime prend en charge nativement les principaux réseaux CDN, notamment :

* Akamai
* Limelight
* Centurylink / Level3
* Contactez votre représentant d’assistance Primetime pour obtenir une liste complète des réseaux de diffusion de contenu pris en charge.

Pour plus d’informations sur le `pttoken` paramètre, voir la description [du paramètre de l’API du](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)Bootstrap.

## Configuration des publicités à diffuser à partir du CDN de contenu {#configure-ad-deliver-from-cdn}

Vous pouvez diffuser des publicités et du contenu à partir du même réseau de diffusion de contenu afin de conserver l’affinité du contenu, de contourner le blocage des publicités et/ou d’optimiser le nombre de connexions requises à partir de l’application cliente. L’Ad Insertion Primetime prend en charge les règles de réécriture de fragments afin de mapper les fragments à votre CDN de contenu.

<!--## Increase start-up performance with your CDN {#increase-startup-performance}

For more information, see [Optimizing start-up](optimize-video-startup-time.md).-->

## Fonctionnalités multiCDN {#enable-multi-cdn-fetures}

Contactez votre représentant du support technique Primetime pour activer les fonctionnalités multi-CDN.
