---
description: Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
title: Contenu des notifications
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---

# Contenu des notifications {#notification-content}

Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.

Votre application peut récupérer la notification et les informations d’état. Vous pouvez également créer un système de journalisation pour les diagnostics et la validation à l’aide des informations de notification.

Vous implémentez des écouteurs d’événements pour capturer les événements et y répondre. De nombreux événements fournissent des `MediaPlayerNotification` notifications d’état.

`MediaPlayerNotification` fournit des informations relatives à l’état du lecteur.

TVSDK fournit une liste chronologique de `MediaPlayerNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic composées des éléments suivants :

   * `type`: INFO, AVERTISSEMENT ou ERREUR.
   * `code`: représentation numérique de la notification.
   * `name`: description lisible par l’utilisateur de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur contenant des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: référence à une autre `MediaPlayerNotification` qui impacte directement cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour la journalisation et la représentation graphique.

## Configuration de votre système de notification {#set-up-your-notification-system}

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

## Ajout de la journalisation et du débogage en temps réel {#add-real-time-logging-and-debugging}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour les diagnostics et la validation sans exagérer le système.

>[!IMPORTANT]
>
>La connexion en arrière-plan ne fait pas partie d’une configuration de production et ne doit pas gérer le trafic à charge élevée. Si votre mise en oeuvre n’a pas besoin d’être absolument terminée, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications.

1. Créez un thread d’exécution basé sur un minuteur pour votre application vidéo qui interroge périodiquement les données collectées par le système de notification TVSDK.

1. Si l’intervalle du minuteur est trop long et que la taille de la liste d’événements est trop petite, la liste d’événements de notification déborde. Pour éviter ce débordement, effectuez l’une des opérations suivantes :

   * Réduisez l’intervalle qui génère le thread qui interroge les nouveaux événements.
   * Augmentez la taille de la liste de notifications.

1. Sérialisez les dernières entrées d’événement de notification au format JSON et envoyez les entrées à un serveur distant pour le posttraitement.

   Le serveur distant peut alors afficher les données fournies sous forme graphique en temps réel.
1. Pour détecter la perte d’événements de notification, recherchez les trous dans la séquence de valeurs d’index d’événement.

   Chaque événement de notification comporte une valeur d’index automatiquement incrémentée par la variable `session.NotificationHistory` classe .

## Balises ID3 {#id-tags}

Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. TVSDK détecte les balises ID3 au niveau du segment du flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .

>[!IMPORTANT]
>
>TVSDK reconnaît les métadonnées ID3 (version 2.3.0 ou 2.4.0) dans les flux audio (AAC) et vidéo (H.264), dans l’un de ses encodages possibles (ASCII, UTF8, UTF16-BE ou UTF16-LE). Il ignore les balises ID3 qui ne se trouvent pas dans l’une des versions ou l’un des formats reconnus. Le codage non spécifié est traité comme UTF8.

Lorsque TVSDK détecte les métadonnées ID3, il émet une notification avec les données suivantes :

* InfoCode = 303007
* TYPE = ID3
* NAME = non présent
* ID = 0

1. Mise en oeuvre d’un écouteur d’événement pour `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` et l’enregistrer auprès de la fonction `MediaPlayer` .

   TVSDK appelle cet écouteur lorsqu’il détecte les métadonnées ID3.

   >[!NOTE]
   >
   >Les repères de publicité personnalisés utilisent le même `onTimedMetadata` pour indiquer la détection d’une nouvelle balise. Cela ne doit pas prêter à confusion, car des signaux publicitaires personnalisés sont détectés au niveau du manifeste et les balises ID3 sont incorporées dans le flux. Pour plus d’informations, voir custom-tags-configure .

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
