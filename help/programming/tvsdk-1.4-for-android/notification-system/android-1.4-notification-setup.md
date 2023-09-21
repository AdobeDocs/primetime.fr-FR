---
description: Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.
title: Configuration de votre système de notification
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Configuration de votre système de notification{#set-up-your-notification-system}

Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.

Le coeur du système de notification du lecteur Primetime est : `Notification` qui représente une notification autonome.

La variable `NotificationHistory` fournit un mécanisme d’accumulation des notifications. Il stocke un journal des objets de notification (NotificationHistoryItem) qui représente une collection de notifications.

Pour recevoir des notifications :

* Écoute des notifications
* Ajout de notifications à l’historique des notifications

1. Prêtez attention aux changements d’état.
1. Mettez en oeuvre le `MediaPlayer.PlaybackEventListener.onStateChanged` rappel.
1. TVSDK transmet deux paramètres au rappel :

   * Le nouvel état ( `MediaPlayer.PlayerState`)
   * A `MediaPlayerNotification` objet

