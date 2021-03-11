---
description: Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.
title: Configuration de votre système de notification
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Configuration de votre système de notification{#set-up-your-notification-system}

Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.

Le coeur du système de notification de Primetime Player est la classe Notification, qui représente une notification autonome.

La classe NotificationHistory fournit un mécanisme permettant d&#39;accumuler des notifications. Il stocke un journal des objets de notification ( `NotificationHistoryItem`) qui représente un ensemble de notifications.

Pour recevoir des notifications :

* Écoute des notifications
* Ajouter des notifications à l’historique des notifications

1. Prêtez attention aux changements d’état.
1. Mettez en oeuvre l’écouteur de événement `MediaPlayer.StatusChangeEvent.STATUS_CHANGED`.
1. TVSDK transmet une instance `MediaPlayer.StatusChangeEvent` à l’écouteur de événement, qui contient deux paramètres :

   * Nouvel état ( `MediaPlayer.Status`)
   * Un objet `MediaPlayerNotification`

