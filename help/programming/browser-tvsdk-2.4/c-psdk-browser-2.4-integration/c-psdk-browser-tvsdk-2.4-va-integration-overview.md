---
description: Vous pouvez effectuer le suivi de l’utilisation des vidéos en intégrant le navigateur TVSDK à Adobe Analytics.
seo-description: Vous pouvez effectuer le suivi de l’utilisation des vidéos en intégrant le navigateur TVSDK à Adobe Analytics.
seo-title: Analyses vidéo
title: Analyses vidéo
uuid: 6351933b-c0f3-4e3e-ad27-bedc8eecc312
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# Analyses vidéo{#video-analytics}

Vous pouvez effectuer le suivi de l’utilisation des vidéos en intégrant le navigateur TVSDK à Adobe Analytics.

Le suivi vidéo dans le navigateur TVSDK utilise le service **Adobe Analytics Video Essentials**, qui fournit des mesures d’engagement vidéo, telles que les vues vidéo, les vidéos terminées, les impressions publicitaires, le temps passé sur la vidéo, etc. Pour plus d&#39;informations sur ce service, contactez votre représentant d&#39;Adobe.

La procédure suivante résume les étapes d’activation du suivi vidéo dans votre lecteur :

1. Initialisez et/ou configurez les composants de suivi vidéo suivants :

   * **Bibliothèque**  AppMeasurement : contient la logique de base de collecte de données de bas niveau. Il s’agit de l’endroit où les données de pulsation vidéo sont accumulées et envoyées sur le réseau.
   * **Bibliothèque**  Video Heartbeat : contient la logique de base de collecte de données Video Heartbeat. La bibliothèque Video Heartbeat accède à un sous-ensemble des API de bibliothèque AppMeasurement.

      >[!TIP]
      >
      >Votre application n’interagit pas directement avec le code de pulsation vidéo. L’application utilise plutôt les API du navigateur TVSDK pour configurer les fonctionnalités de suivi vidéo de votre lecteur.

   * **Bibliothèque**  d’identifiants visiteur : identifie de manière unique les visiteurs sur la page Web qui héberge le lecteur vidéo.
   >[!IMPORTANT]
   >
   >La fonctionnalité de suivi vidéo intégrée du SDK du navigateur dépend d’une instance AppMeasurement correctement configurée. Les éléments de suivi supposent que la bibliothèque AppMeasurement est déjà instanciée et configurée avant de configurer et d’activer le suivi vidéo. Les fonctionnalités de suivi vidéo du SDK du navigateur dépendent de l’existence d’une instance entièrement fonctionnelle et correctement configurée de la bibliothèque AppMeasurement.

1. Configurez le rapports d’analyses vidéo côté serveur à l’aide des outils d’administration Adobe Analytics.