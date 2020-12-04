---
description: Vous pouvez suivre l’utilisation des vidéos en intégrant TVSDK à Adobe Analytics.
seo-description: Vous pouvez suivre l’utilisation des vidéos en intégrant TVSDK à Adobe Analytics.
seo-title: Analyses vidéo
title: Analyses vidéo
uuid: c3cb0574-1117-409c-8aa7-641363d8d85f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Analyses vidéo{#video-analytics}

Vous pouvez suivre l’utilisation des vidéos en intégrant TVSDK à Adobe Analytics.

Le suivi vidéo dans TVSDK utilise le service **Adobe Analytics Video Essentials**, qui fournit des mesures d’engagement vidéo, telles que les vues vidéo, les vidéos terminées, les impressions publicitaires, le temps passé sur la vidéo, etc. Pour plus d&#39;informations sur ce service, contactez votre représentant d&#39;Adobe.

La procédure suivante résume les étapes d’activation du suivi vidéo dans votre lecteur :

1. Initialisez et/ou configurez les composants de suivi vidéo suivants :

   * **Bibliothèque**  AppMeasurement : contient la logique de base de collecte de données de bas niveau. Il s’agit de l’endroit où les données de pulsation vidéo sont accumulées et envoyées sur le réseau.
   * **Bibliothèque**  Video Heartbeat : contient la logique de base de collecte de données Video Heartbeat. La bibliothèque Video Heartbeat accède à un sous-ensemble des API de bibliothèque `AppMeasurement`.

      >[!TIP]
      >
      >Votre application n’interagit pas directement avec le code de pulsation vidéo. L’application utilise plutôt les API TVSDK pour configurer les fonctionnalités de suivi vidéo de votre lecteur.

   * **Bibliothèque**  d’identifiants visiteur : identifie de manière unique les visiteurs sur la page Web qui héberge le lecteur vidéo.
   >[!IMPORTANT]
   >
   >La fonctionnalité de suivi vidéo intégrée TVSDK dépend d’une instance `AppMeasurement` correctement configurée. Les éléments de suivi supposent que la bibliothèque `AppMeasurement` est déjà instanciée et configurée avant de configurer et d&#39;activer le suivi vidéo. Les fonctionnalités de suivi vidéo TVSDK dépendent de l’existence d’une instance entièrement fonctionnelle et correctement configurée de la bibliothèque `AppMeasurement`.

1. Configurez le rapports d’analyses vidéo côté serveur à l’aide des outils d’administration Adobe Analytics.

