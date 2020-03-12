---
description: Les  et notifications vous aident à gérer les aspects asynchrones de l’application vidéo.
seo-description: Les  et notifications vous aident à gérer les aspects asynchrones de l’application vidéo.
seo-title: Notifications et  de l’état du lecteur, , erreurs et consignation
title: Notifications et  de l’état du lecteur, , erreurs et consignation
uuid: c4a108e7-72aa-4c96-9538-b1385343d6af
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Notifications et  de l’état du lecteur, , erreurs et consignation {#notifications-and-events-for-player-status-activity-errors-and-logging}

Les  et notifications vous aident à gérer les aspects asynchrones de l’application vidéo.

`MediaPlayerStatus` fournit des informations sur les modifications de l’état du lecteur. `Notification` fournit des informations sur les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur. Vous implémentez des écouteurs  pour capturer et répondre aux  de ( `MediaPlayerEvent` objets).

Votre application peut récupérer les informations de notification et d’état. Grâce à ces informations, vous pouvez également créer un système de journalisation pour les diagnostics et la validation.

## Contenu de notification {#section_DF951FF601794CF592841BB7406DC1A1}

`MediaPlayerNotification` fournit des informations relatives à l’état du lecteur.

TVSDK fournit un chronologique des `MediaPlayerNotification` notifications et chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic composées des éléments suivants :

   * `type`: INFORMATIONS, AVERTISSEMENT ou ERREUR.
   * `code`: Représentation numérique de la notification.
   * `name`: Description lisible de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur qui contient des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: Référence à un autre `MediaPlayerNotification` objet qui affecte directement cette notification.

Vous pouvez stocker ces informations en local pour  plus tard  ou les envoyer à un serveur distant pour la journalisation et la représentation graphique.

## Configuration de votre système de notification {#section_9E37C09ECFA54B3DA8D3AA9ED1BAFC17}

Vous pouvez écouter les notifications.

Le coeur du système de notification de Primetime Player est la `Notification` classe, qui représente une notification autonome.

Pour recevoir des notifications, écoutez les notifications comme suit :

1. Implémentez le `NotificationEventListener.onNotification()` rappel.
1. TVSDK transmet un `NotificationEvent` objet au rappel.

   >[!NOTE]
   >
   >Les types de notifications sont énumérés dans l’ `Notification.Type` énumération :

   * `ERROR`
   * `INFO`
   * `WARNING`

## Ajouter journalisation et débogage en temps réel {#section_9D4004308CB243AD9B50818895D10005}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour le diagnostic et la validation sans insister sur le système.

>[!IMPORTANT]
>
>La connexion n’est pas incluse dans une configuration de production et ne devrait pas gérer le trafic à fort chargement. Si votre implémentation n’a pas besoin d’être absolument terminée, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications :

1. Créez un thread d’exécution basé sur le minuteur pour votre application vidéo qui  périodiquement les données rassemblées par le système de notification TVSDK.
1. Si l’intervalle du minuteur est trop long et que la taille du  est trop petite, l’ de l’ de l’ de la de notification déborde.

   >[!NOTE]
   >
   >Pour éviter ce débordement, effectuez l’une des opérations suivantes :    >
   >    
   >    
   >    1. Réduisez l’intervalle de temps qui déclenche le thread qui interroge les nouveaux .
   >    1. Augmentez la taille du de notification.


1. Sérialisez les entrées de de notification les plus récentes au format JSON et envoyez les entrées à un serveur distant pour le post-traitement.

   >[!NOTE]
   >
   >Le serveur distant peut afficher les données fournies sous forme graphique en temps réel.

1. Pour détecter la perte des  de notification, recherchez les lacunes dans la séquence des valeurs d’index de .