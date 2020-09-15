---
description: Les événements et notifications vous aident à gérer les aspects asynchrones de l’application vidéo.
seo-description: Les événements et notifications vous aident à gérer les aspects asynchrones de l’application vidéo.
seo-title: Notifications et événements concernant l’état, l’activité, les erreurs et la consignation du lecteur
title: Notifications et événements concernant l’état, l’activité, les erreurs et la consignation du lecteur
uuid: c4a108e7-72aa-4c96-9538-b1385343d6af
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Notifications et événements concernant l’état, l’activité, les erreurs et la consignation du lecteur {#notifications-and-events-for-player-status-activity-errors-and-logging}

Les événements et notifications vous aident à gérer les aspects asynchrones de l’application vidéo.

`MediaPlayerStatus` fournit des informations sur les modifications de l’état du lecteur. `Notification` fournit des informations sur les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo modifient également l’état du lecteur. Vous implémentez des écouteurs de événement pour capturer les événements ( `MediaPlayerEvent` objets) et y répondre.

Votre application peut récupérer les informations de notification et d’état. Grâce à ces informations, vous pouvez également créer un système de journalisation pour les diagnostics et la validation.

## Contenu de la notification {#section_DF951FF601794CF592841BB7406DC1A1}

`MediaPlayerNotification` fournit des informations relatives à l’état du lecteur.

TVSDK fournit une liste chronologique des `MediaPlayerNotification` notifications et chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic comprenant les éléments suivants :

   * `type`: INFORMATIONS, AVERTISSEMENT ou ERREUR.
   * `code`: Représentation numérique de la notification.
   * `name`: Description lisible de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur qui contient des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: Référence à un autre `MediaPlayerNotification` objet qui a un impact direct sur cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour consigner et représenter graphiquement.

## Configuration de votre système de notification {#section_9E37C09ECFA54B3DA8D3AA9ED1BAFC17}

Vous pouvez écouter les notifications.

Le coeur du système de notification de Primetime Player est la `Notification` classe, qui représente une notification autonome.

Pour recevoir des notifications, écoutez les notifications comme suit :

1. Implémentez le `NotificationEventListener.onNotification()` rappel.
1. TVSDK transmet un `NotificationEvent` objet au rappel.

   >[!NOTE]
   >
   >Les types de notifications sont énumérés dans l&#39; `Notification.Type` énumération :

   * `ERROR`
   * `INFO`
   * `WARNING`

## ajouter la journalisation et le débogage en temps réel {#section_9D4004308CB243AD9B50818895D10005}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour les diagnostics et les validations sans insister sur le système.

>[!IMPORTANT]
>
>L’extrémité arrière de la journalisation ne fait pas partie d’une configuration de production et ne devrait pas gérer le trafic à forte charge. Si votre implémentation n’a pas besoin d’être complète, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications :

1. Créez un thread d’exécution basé sur un minuteur pour votre application vidéo qui requête périodiquement les données collectées par le système de notification TVSDK.
1. Si l’intervalle du minuteur est trop long et que la taille de la liste du événement est trop petite, la liste du événement de notification déborde.

   >[!NOTE]
   >
   >Pour éviter ce débordement, effectuez l’une des opérations suivantes :
   >
   >1. Réduisez l&#39;intervalle de temps qui conduit le thread qui effectue l&#39;interrogation des nouveaux événements.
      >
      >
   1. Augmentez la taille de la liste de notification.


1. Sérialisez les dernières entrées du événement de notification au format JSON et envoyez les entrées à un serveur distant pour post-traitement.

   >[!NOTE]
   >
   >Le serveur distant peut afficher les données fournies sous forme graphique en temps réel.

1. Pour détecter la perte de événements de notification, recherchez des lacunes dans la séquence de valeurs d’index de événement.