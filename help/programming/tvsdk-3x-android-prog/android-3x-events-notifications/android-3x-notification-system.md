---
description: Les événements et notifications vous aident à gérer les aspects asynchrones de l’application vidéo.
title: Notifications et événements concernant l’état, l’activité, les erreurs et la journalisation du lecteur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notifications et événements concernant l’état, l’activité, les erreurs et la journalisation du lecteur {#notifications-and-events-for-player-status-activity-errors-and-logging}

Les événements et notifications vous aident à gérer les aspects asynchrones de l’application vidéo.

`MediaPlayerStatus` fournit des informations sur les modifications de l’état du lecteur. `Notification` fournit des informations sur les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur. Vous implémentez des écouteurs d’événements pour capturer les événements et y répondre ( `MediaPlayerEvent` ).

Votre application peut récupérer les informations de notification et d’état. Grâce à ces informations, vous pouvez également créer un système de journalisation pour les diagnostics et la validation.

## Contenu des notifications {#section_DF951FF601794CF592841BB7406DC1A1}

`MediaPlayerNotification` fournit des informations relatives à l’état du lecteur.

TVSDK fournit une liste chronologique de `MediaPlayerNotification` et chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic composées des éléments suivants :

   * `type`: INFO, AVERTISSEMENT ou ERREUR.
   * `code`: représentation numérique de la notification.
   * `name`: description lisible par l’utilisateur de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur contenant des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: référence à une autre `MediaPlayerNotification` qui impacte directement cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour la journalisation et la représentation graphique.

## Configuration de votre système de notification {#section_9E37C09ECFA54B3DA8D3AA9ED1BAFC17}

Vous pouvez écouter les notifications.

Le coeur du système de notification du lecteur Primetime est : `Notification` qui représente une notification autonome.

Pour recevoir des notifications, écoutez les notifications comme suit :

1. Mettez en oeuvre le `NotificationEventListener.onNotification()` rappel.
1. TVSDK transmet une `NotificationEvent` à l’objet callback.

   >[!NOTE]
   >
   >Les types de notifications sont répertoriés dans la variable `Notification.Type` enum :

   * `ERROR`
   * `INFO`
   * `WARNING`

## Ajout de la journalisation et du débogage en temps réel {#section_9D4004308CB243AD9B50818895D10005}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour les diagnostics et la validation sans appuyer sur le système.

>[!IMPORTANT]
>
>La connexion en arrière-plan ne fait pas partie d’une configuration de production et ne doit pas gérer le trafic à charge élevée. Si votre mise en oeuvre n’a pas besoin d’être absolument terminée, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications :

1. Créez un thread d’exécution basé sur un minuteur pour votre application vidéo qui interroge périodiquement les données collectées par le système de notification TVSDK.
1. Si l’intervalle du minuteur est trop long et que la taille de la liste d’événements est trop petite, la liste d’événements de notification déborde.

   >[!NOTE]
   >
   >Pour éviter ce débordement, effectuez l’une des opérations suivantes :
   >
   >1. Réduisez l’intervalle qui génère le thread qui interroge les nouveaux événements.
   >
   >1. Augmentez la taille de la liste de notifications.

1. Sérialisez les dernières entrées d’événement de notification au format JSON et envoyez les entrées à un serveur distant pour le posttraitement.

   >[!NOTE]
   >
   >Le serveur distant peut afficher les données fournies sous forme graphique en temps réel.

1. Pour détecter la perte d’événements de notification, recherchez les trous dans la séquence de valeurs d’index d’événement.
