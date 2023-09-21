---
description: Pour tenir compte des clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte les mesures d’utilisation et les utilise pour déterminer le montant de facturation des clients.
title: Mesures de facturation
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Présentation {#billing-metrics-overview}

Pour tenir compte des clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte les mesures d’utilisation et les utilise pour déterminer le montant de facturation des clients.

Chaque fois que le lecteur génère un événement de démarrage de flux, le TVSDK du navigateur commence à envoyer des messages HTTP périodiquement au système de facturation de l’Adobe. La période, appelée durée facturable, peut être différente pour le contenu VOD standard, le pro VOD (publicités mid-roll activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

Les messages contiennent les informations suivantes :

* Type de contenu (actif, linéaire ou VOD)
* URL de contenu
* Si les publicités sont activées
* Si les publicités mid-roll sont activées (VOD uniquement)
* Si le flux est protégé par DRM
* Version et plateforme du navigateur TVSDK

Adobe préconfigure cette disposition, mais si vous souhaitez la modifier, contactez votre représentant d’activation d’Adobe.

Pour surveiller les statistiques envoyées par le navigateur TVSDK à Adobe, obtenez l’URL auprès de votre représentant d’activation de l’Adobe et utilisez un outil de capture réseau, par exemple Charles, pour afficher les données.
