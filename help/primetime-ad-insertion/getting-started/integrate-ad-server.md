---
title: Intégration de votre serveur d’annonces
description: Intégration de votre serveur d’annonces
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Intégration de votre serveur d’annonces {#integrate-ad-server}

Pour commencer, vous disposez d’un identifiant de connexion pour accéder à la console de l’Ad Insertion Primetime, dans laquelle vous configurez les règles utilisées par l’Ad Insertion Primetime pour transférer les requêtes de publicité vers le serveur de publicités de votre choix. L’Ad Insertion Primetime prend en charge la plupart des serveurs d’annonces compatibles VAST ou VMAP.

>[!NOTE]
>
>[Page VAST IAB](https://www.iab.com/guidelines/digital-video-ad-serving-template-vast)

## Prise en charge des macros {#macro-support}

Primetime Ad Insertion active les macros de serveur de publicités suivantes pour tous les flux :

* Blocage du cache
* Contexte de l’application ou URL de la page
* Durée moyenne
* Ressource vidéo actuelle

Si d’autres macros sont nécessaires, contactez votre représentant du support Adobe Primetime.

## Fonctionnalités avancées {#advanced-features}

Primetime Ad Insertion est également doté d’une prise de décision basée sur des règles qui permet des fonctionnalités avancées. Cela peut s’avérer important si vous souhaitez acheminer des publicités vers différents serveurs d’annonces en fonction des droits d’inventaire ou activer la limitation de fréquence pour les publicités individuelles. Pour plus d’informations, voir [Fonctionnalités avancées](/help/primetime-ad-insertion/advanced-features/route-ads-based-on-rules.md).
