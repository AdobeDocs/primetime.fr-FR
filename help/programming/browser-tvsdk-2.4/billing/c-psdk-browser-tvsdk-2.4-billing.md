---
description: Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.
seo-description: Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.
seo-title: Mesures de facturation
title: Mesures de facturation
uuid: e09b77b3-89d3-44d6-be4e-e1612fbf89fc
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#billing-metrics-overview}

Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.

Chaque fois que le lecteur génère un événement de début de diffusion en continu, le navigateur TVSDK début à envoyer régulièrement des messages HTTP au système de facturation d’Adobe. La période, appelée durée facturable, peut être différente pour le contenu VOD standard, le contenu pro VOD (publicités mid-roll activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

Les messages contiennent les informations suivantes :

* Type de contenu (dynamique, linéaire ou VOD)
* URL de contenu
* Activation ou non des publicités
* Activation ou non des publicités preroll moyennes (VOD uniquement)
* Si le flux est protégé par DRM
* Version et plate-forme du kit de développement logiciel (SDK) du navigateur

Adobe préconfigure cet arrangement, mais si vous souhaitez le modifier, contactez votre représentant Adobe Enablement.

Pour contrôler les statistiques que le navigateur TVSDK envoie à Adobe, obtenez l’URL auprès de votre représentant Adobe Enablement et utilisez un outil de capture réseau, par exemple Charles, pour afficher les données.
