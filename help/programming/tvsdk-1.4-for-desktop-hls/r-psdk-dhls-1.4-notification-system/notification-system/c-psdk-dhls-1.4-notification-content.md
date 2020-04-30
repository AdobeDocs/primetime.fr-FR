---
description: MediaPlayerNotification fournit des informations relatives à l’état du lecteur.
seo-description: MediaPlayerNotification fournit des informations relatives à l’état du lecteur.
seo-title: Contenu de la notification
title: Contenu de la notification
uuid: c2321a49-1b60-4e44-b8e2-a023b764d779
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Contenu de la notification{#notification-content}

MediaPlayerNotification fournit des informations relatives à l’état du lecteur.

TVSDK fournit une liste chronologique des `MediaPlayerNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic comprenant les éléments suivants :

   * tapez INFO, WARN ou ERROR
   * `code`: Représentation numérique de la notification.
   * `name`: Description lisible de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur qui contient des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: Référence à un autre `MediaPlayerNotification` objet qui a un impact direct sur cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour consigner et représenter graphiquement.
