---
description: Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, l’Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.
seo-description: Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, l’Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.
seo-title: Mesures de facturation
title: Mesures de facturation
uuid: 4a03995a-60f6-440e-9cdf-9c0b9c5f1d90
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Aperçu {#billing-metrics-overview}

Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, l’Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.

Chaque fois que le lecteur génère un événement de début de flux, TVSDK début à envoyer des messages HTTP régulièrement au système de facturation de l&#39;Adobe. La période, appelée durée facturable, peut être différente pour le contenu VOD standard, le contenu pro VOD (publicités mid-roll activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec l’Adobe détermine les valeurs réelles.

Les messages contiennent les informations suivantes :

* Type de contenu (dynamique, linéaire ou VOD)
* URL de contenu
* Activation ou non des publicités
* Activation ou non des publicités preroll moyennes (VOD uniquement)
* Si le flux est protégé par DRM
* Version et plate-forme du SDK TVSDK

L’Adobe préconfigure cette disposition, mais vous pouvez collaborer avec votre représentant d’Adobe Enablement pour modifier l’arrangement, travailler avec votre représentant d’Adobe Enablement.

Pour surveiller les statistiques envoyées par TVSDK à l’Adobe, obtenez l’URL auprès de votre représentant d’activation d’Adobe et utilisez un outil de capture réseau, comme Charles, pour voir les données.
