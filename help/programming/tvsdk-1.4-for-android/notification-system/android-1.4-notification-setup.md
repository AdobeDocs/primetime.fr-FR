---
description: Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.
title: Configuration de votre système de notification
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
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

