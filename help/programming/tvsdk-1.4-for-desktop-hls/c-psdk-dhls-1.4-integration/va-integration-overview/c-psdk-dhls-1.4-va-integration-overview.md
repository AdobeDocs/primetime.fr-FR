---
description: Vous pouvez effectuer le suivi de l’utilisation de la vidéo en intégrant TVSDK à Adobe Analytics.
title: Analyses vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Analyses vidéo{#video-analytics}

Vous pouvez effectuer le suivi de l’utilisation de la vidéo en intégrant TVSDK à Adobe Analytics.

Le suivi vidéo dans TVSDK utilise la méthode **Principes fondamentaux des vidéos Adobe Analytics** service qui fournit des mesures d’engagement vidéo, telles que les affichages de vidéos, les vidéos terminées, les impressions publicitaires, le temps passé sur la vidéo, etc. Pour plus d’informations sur ce service, contactez votre représentant Adobe.

La procédure suivante résume les étapes d’activation du suivi vidéo dans votre lecteur :

1. Initialisez et/ou configurez les composants de suivi vidéo suivants :

   * **Bibliothèque d’AppMeasurements** - Contient la logique de base de la collecte de données de bas niveau. C’est là que les données de pulsation vidéo sont accumulées et envoyées sur le réseau.
   * **Bibliothèque Video Heartbeat** - Contient la logique de base de la collecte de données de la pulsation vidéo. La bibliothèque Video Heartbeat accède à un sous-ensemble de la variable `AppMeasurement` API de bibliothèque.

     >[!TIP]
     >
     >Votre application n’interagit pas directement avec le code de pulsation vidéo. À la place, l’application utilise les API TVSDK pour configurer les fonctionnalités de suivi vidéo de votre lecteur.

   * **Bibliothèque VisitorID** - Identifie de manière unique les visiteurs de la page web qui héberge le lecteur vidéo.

   >[!IMPORTANT]
   >
   >La fonctionnalité de suivi vidéo intégrée de TVSDK dépend d’une configuration correcte. `AppMeasurement` instance. Les éléments de suivi supposent que la variable `AppMeasurement` est déjà instanciée et configurée avant de configurer et d’activer le suivi vidéo. Les fonctionnalités de suivi vidéo TVSDK dépendent de l’existence d’une instance entièrement fonctionnelle et correctement configurée du `AppMeasurement` bibliothèque .

1. Configurez les rapports d’analyse vidéo côté serveur à l’aide des outils d’administration Adobe Analytics.
