---
description: MediaPlayerNotification fournit des informations relatives à l’état du lecteur.
title: Contenu de la notification
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Contenu de la notification{#notification-content}

MediaPlayerNotification fournit des informations relatives à l’état du lecteur.

TVSDK fournit une liste chronologique de `MediaPlayerNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic comprenant les éléments suivants :

   * tapez INFO, WARN ou ERROR
   * `code`: Représentation numérique de la notification.
   * `name`: Description lisible de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur qui contient des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: Référence à un autre  `MediaPlayerNotification` objet qui a un impact direct sur cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour consigner et représenter graphiquement.
