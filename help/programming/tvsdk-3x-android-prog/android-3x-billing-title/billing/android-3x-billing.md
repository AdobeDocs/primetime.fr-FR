---
description: Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.
seo-description: Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.
seo-title: Mesures de facturation
title: Mesures de facturation
uuid: 6ae9eb1e-4b03-467f-b80a-96313bd01543
translation-type: tm+mt
source-git-commit: ''

---


# Mesures de facturation {#billing-metrics}

Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.

Chaque fois que le lecteur génère un événement de début de diffusion en continu, TVSDK début à envoyer régulièrement des messages HTTP au système de facturation d’Adobe. La période, appelée durée facturable, peut être différente pour le contenu VOD standard, le contenu pro VOD (publicités mid-roll activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

Les messages contiennent les informations suivantes :

* Type de contenu (dynamique, linéaire ou VOD)
* URL de contenu
* Activation ou non des publicités
* Activation ou non des publicités preroll moyennes (VOD uniquement)
* Si le flux est protégé par DRM
* Version et plate-forme du SDK TVSDK

Adobe préconfigure cet arrangement, mais vous pouvez collaborer avec votre représentant Adobe Enablement pour le modifier, en collaboration avec votre représentant Adobe Enablement.

Pour contrôler les statistiques envoyées par TVSDK à Adobe, obtenez l’URL auprès de votre représentant Adobe Enablement et utilisez un outil de capture réseau, tel que Charles, pour afficher les données.