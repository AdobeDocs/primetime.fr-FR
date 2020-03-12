---
description: Vous pouvez suivre l’utilisation de la vidéo en intégrant TVSDK à Adobe Analytics.
seo-description: Vous pouvez suivre l’utilisation de la vidéo en intégrant TVSDK à Adobe Analytics.
seo-title: Analyse vidéo
title: Analyse vidéo
uuid: c3cb0574-1117-409c-8aa7-641363d8d85f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Analyse vidéo{#video-analytics}

Vous pouvez suivre l’utilisation de la vidéo en intégrant TVSDK à Adobe Analytics.

Le suivi vidéo dans TVSDK utilise le service **Adobe Analytics Video Essentials** , qui fournit des mesures d’engagement vidéo, telles que les  vidéo, les vidéos terminées, les impressions publicitaires, le temps passé sur la vidéo, etc. Pour plus d’informations sur ce service, contactez votre représentant Adobe.

La procédure suivante récapitule les étapes d’activation du suivi vidéo dans votre lecteur :

1. Initialisez et/ou configurez les composants de suivi vidéo suivants :

   * **Bibliothèque** AppMeasurement : contient la logique de base de collecte de données de bas niveau. C’est là que les données de pulsation vidéo sont accumulées et envoyées sur le réseau.
   * **Bibliothèque** de pulsation vidéo : contient la logique de base de collecte de données de pulsation vidéo. La bibliothèque Video Heartbeat accède à un sous-ensemble des API de `AppMeasurement` bibliothèque.

      >[!TIP]
      >
      >Votre application n’interagit pas directement avec le code de pulsation vidéo. L’application utilise plutôt les API TVSDK pour configurer les fonctionnalités de suivi vidéo de votre lecteur.

   * **Bibliothèque** d’identifiants visiteur : identifie de manière unique les de la page Web qui héberge le lecteur vidéo.
   >[!IMPORTANT]
   >
   >La fonctionnalité de suivi vidéo intégrée de TVSDK dépend d’une `AppMeasurement` instance correctement configurée. Les éléments de suivi supposent que la `AppMeasurement` bibliothèque est déjà instanciée et configurée avant de configurer et d’activer le suivi vidéo. Les fonctionnalités de suivi vidéo TVSDK dépendent de l’existence d’une instance de la `AppMeasurement` bibliothèque entièrement fonctionnelle et correctement configurée.

1. Configurez le d’analyses vidéo côté serveur à l’aide des outils d’administration d’Adobe Analytics.

