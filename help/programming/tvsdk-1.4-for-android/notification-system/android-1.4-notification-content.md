---
description: Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
seo-description: Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
seo-title: Contenu de notification
title: Contenu de notification
uuid: 89fb8f63-b0d5-45cd-bdad-348529fd07d0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Contenu de notification {#notification-content}

Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.

Votre application peut récupérer la notification et les informations d’état. Vous pouvez également créer un système de journalisation pour les diagnostics et la validation à l’aide des informations de notification.

Vous implémentez des écouteurs  pour capturer et répondre aux  de. De nombreux  fournissent des notifications `MediaPlayerNotification` d’état.

`MediaPlayerNotification` fournit des informations relatives à l’état du lecteur.

TVSDK fournit un chronologique des `MediaPlayerNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic composées des éléments suivants :

   * `type`: INFORMATIONS, AVERTISSEMENT ou ERREUR.
   * `code`: Représentation numérique de la notification.
   * `name`: Description lisible de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur qui contient des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: Référence à un autre `MediaPlayerNotification` objet qui affecte directement cette notification.

Vous pouvez stocker ces informations en local pour  plus tard  ou les envoyer à un serveur distant pour la journalisation et la représentation graphique.

## Configuration de votre système de notification {#set-up-your-notification-system}

Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications.

Le coeur du système de notification de Primetime Player est la `Notification` classe, qui représente une notification autonome.

La `NotificationHistory` classe fournit un mécanisme permettant d’accumuler des notifications. Il stocke un journal des objets Notification (NotificationHistoryItem) qui représente une collection de notifications.

Pour recevoir des notifications :

* Écoute des notifications
* Ajouter de notifications à l’historique des notifications

1. Prêtez attention aux changements d’état.
1. Implémentez le `MediaPlayer.PlaybackEventListener.onStateChanged` rappel.
1. TVSDK transmet deux paramètres au rappel :

   * Le nouvel état ( `MediaPlayer.PlayerState`)
   * Un `MediaPlayerNotification` objet

## Ajouter journalisation et débogage en temps réel {#add-real-time-logging-and-debugging}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour les diagnostics et la validation sans trop insister sur le système.

>[!IMPORTANT]
>
>La connexion n’est pas incluse dans une configuration de production et ne devrait pas gérer le trafic à fort chargement. Si votre implémentation n’a pas besoin d’être absolument terminée, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications.

1. Créez un thread d’exécution basé sur le minuteur pour votre application vidéo qui  périodiquement les données rassemblées par le système de notification TVSDK.

1. Si l’intervalle du minuteur est trop long et que la taille du  de est trop petite, l’ de la  de notification  débordera. Pour éviter ce débordement, effectuez l’une des opérations suivantes :

   * Réduisez l’intervalle de temps qui déclenche le thread qui interroge les nouveaux .
   * Augmentez la taille du de notification.

1. Sérialisez les entrées de de notification les plus récentes au format JSON et envoyez les entrées à un serveur distant pour le post-traitement.

   Le serveur distant peut alors afficher les données fournies sous forme graphique en temps réel.
1. Pour détecter la perte des  de notification, recherchez les lacunes dans la séquence des valeurs d’index de .

   Chaque  de notification comporte une valeur d’index automatiquement incrémentée par la `session.NotificationHistory` classe.

## Balises ID3 {#id-tags}

Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. TVSDK détecte les balises ID3 au niveau du segment de flux de transport (TS) dans les flux HLS et distribue un  de. L’application peut extraire des données de la balise .

>[!IMPORTANT]
>
>TVSDK reconnaît les métadonnées ID3 (version 2.3.0 ou 2.4.0) dans les flux audio (AAC) et vidéo (H.264), dans n’importe quel encodage possible (ASCII, UTF8, UTF16-BE ou UTF16-LE). Il ignore les balises ID3 qui ne sont pas dans l’une des versions ou des formats reconnus. Le codage non spécifié est traité comme UTF8.

Lorsque TVSDK détecte les métadonnées ID3, il émet une notification avec les données suivantes :

* InfoCode = 303007
* TYPE = ID3
* NAME = absent
* ID = 0

1. Implémentez un écouteur de  pour `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` et enregistrez-le avec l’ `MediaPlayer` objet.

   TVSDK appelle cet écouteur lorsqu’il détecte les métadonnées ID3.

   >[!NOTE]
   >
   >Les signaux publicitaires personnalisés utilisent le même `onTimedMetadata` pour indiquer la détection d’une nouvelle balise. Cela ne doit pas entraîner de confusion, car des signaux publicitaires personnalisés sont détectés au niveau du manifeste et les balises ID3 sont intégrées dans le flux. Pour plus d’informations, voir custom-tags-configure .

1. Récupérez les métadonnées.

   ```java
   @Override 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       TimedMetadata.Type type = timedMetadata.getType(); 
       if (type.equals(TimedMetadata.Type.ID3)){ 
           long time = timeMetadata.getTime(); 
           Metadata metadata = timedMetadata.getMetadata(); 
           Set<String> keys = metadata.keySet(); 
           for (String key : keys){ 
               String value = metadata.getValue(key); 
           } 
       } 
   }
   ```
