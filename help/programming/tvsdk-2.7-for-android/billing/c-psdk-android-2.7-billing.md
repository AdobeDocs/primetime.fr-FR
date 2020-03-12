---
description: Afin d’accommoder les clients qui souhaitent payer uniquement ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.
seo-description: Afin d’accommoder les clients qui souhaitent payer uniquement ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.
seo-title: Mesures de facturation
title: Mesures de facturation
uuid: 4a03995a-60f6-440e-9cdf-9c0b9c5f1d90
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#billing-metrics-overview}

Afin d’accommoder les clients qui souhaitent payer uniquement ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.

Chaque fois que le lecteur génère un de flux  , TVSDKenvoie des messages HTTP régulièrement au système de facturation d’Adobe. La période, connue sous le nom de durée facturable, peut être différente pour le contenu VOD standard, le contenu pro VOD (publicités milieu de gamme activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

Les messages contiennent les informations suivantes :

* Type de contenu (dynamique, linéaire ou VOD)
* URL de contenu
* Activation ou non des publicités
* Activation ou non des publicités moyennes (VOD uniquement)
* Protection du flux par DRM
* Version et plate-forme du SDK TVSDK

Adobe préconfigure cet arrangement, mais vous pouvez travailler avec votre représentant Adobe Enablement pour le modifier, en collaboration avec votre représentant Adobe Enablement.

Pour surveiller les statistiques envoyées par TVSDK à Adobe, obtenez l’URL auprès de votre représentant Adobe Enablement et utilisez un outil de capture réseau, comme Charles, pour afficher les données.
