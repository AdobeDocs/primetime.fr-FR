---
description: Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.
seo-description: Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.
seo-title: Configuration de votre système de notification
title: Configuration de votre système de notification
uuid: caa6a306-dea9-45ee-b0b3-569b5f2527a1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Configuration de votre système de notification{#set-up-your-notification-system}

Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.

Le coeur du système de notification de Primetime Player est la classe `Notification`, qui représente une notification autonome.

La classe `NotificationHistory` fournit un mécanisme permettant d&#39;accumuler des notifications. Il stocke un journal des objets Notification (NotificationHistoryItem) qui représente une collection de notifications.

Pour recevoir des notifications :

* Écoute des notifications
* Ajouter des notifications à l’historique des notifications

1. Prêtez attention aux changements d’état.
1. Implémentez le rappel `MediaPlayer.PlaybackEventListener.onStateChanged`.
1. TVSDK transmet deux paramètres au rappel :

   * Nouvel état ( `MediaPlayer.PlayerState`)
   * Un objet `MediaPlayerNotification`

