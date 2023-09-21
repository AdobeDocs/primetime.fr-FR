---
description: Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.
title: Configuration de votre système de notification
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Configuration de votre système de notification{#set-up-your-notification-system}

Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.

Le coeur du système de notification du lecteur Primetime est la classe Notification, qui représente une notification autonome.

La classe NotificationHistory fournit un mécanisme d’accumulation des notifications. Il stocke un journal des notifications ( `NotificationHistoryItem`) qui représente une collection de notifications.

Pour recevoir des notifications :

* Écoute des notifications
* Ajout de notifications à l’historique des notifications

1. Prêtez attention aux changements d’état.
1. Mettez en oeuvre le `MediaPlayer.StatusChangeEvent.STATUS_CHANGED` écouteur d’événement.
1. TVSDK transmet une `MediaPlayer.StatusChangeEvent` à l’écouteur d’événement, qui contient deux paramètres :

   * Le nouvel état ( `MediaPlayer.Status`)
   * A `MediaPlayerNotification` objet
