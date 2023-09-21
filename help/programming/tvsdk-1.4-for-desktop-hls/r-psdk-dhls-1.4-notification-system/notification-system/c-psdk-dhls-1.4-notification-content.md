---
description: MediaPlayerNotification fournit des informations relatives à l’état du lecteur.
title: Contenu des notifications
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Contenu des notifications{#notification-content}

MediaPlayerNotification fournit des informations relatives à l’état du lecteur.

TVSDK fournit une liste chronologique de `MediaPlayerNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic composées des éléments suivants :

   * type INFO, WARN ou ERROR
   * `code`: représentation numérique de la notification.
   * `name`: description lisible par l’utilisateur de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur contenant des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: référence à une autre `MediaPlayerNotification` qui impacte directement cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour la journalisation et la représentation graphique.
