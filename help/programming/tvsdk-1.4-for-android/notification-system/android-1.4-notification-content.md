---
description: Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo modifient également l’état du lecteur.
seo-description: Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo modifient également l’état du lecteur.
seo-title: Contenu de la notification
title: Contenu de la notification
uuid: 89fb8f63-b0d5-45cd-bdad-348529fd07d0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# Contenu de la notification {#notification-content}

Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo modifient également l’état du lecteur.

Votre application peut récupérer la notification et les informations d’état. Vous pouvez également créer un système de journalisation pour les diagnostics et la validation à l’aide des informations de notification.

Vous implémentez des écouteurs de événement pour capturer les événements et y répondre. De nombreux événements fournissent des notifications d’état `MediaPlayerNotification`.

`MediaPlayerNotification` fournit des informations relatives à l’état du lecteur.

TVSDK fournit une liste chronologique de `MediaPlayerNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic comprenant les éléments suivants :

   * `type`: INFORMATIONS, AVERTISSEMENT ou ERREUR.
   * `code`: Représentation numérique de la notification.
   * `name`: Description lisible de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur qui contient des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: Référence à un autre  `MediaPlayerNotification` objet qui a un impact direct sur cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour consigner et représenter graphiquement.

## Configuration de votre système de notification {#set-up-your-notification-system}

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

## Ajouter la journalisation et le débogage en temps réel {#add-real-time-logging-and-debugging}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour les diagnostics et les validations sans trop insister sur le système.

>[!IMPORTANT]
>
>L’extrémité arrière de la journalisation ne fait pas partie d’une configuration de production et ne devrait pas gérer le trafic à forte charge. Si votre implémentation n’a pas besoin d’être complète, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications.

1. Créez un thread d’exécution basé sur un minuteur pour votre application vidéo qui requête périodiquement les données collectées par le système de notification TVSDK.

1. Si l’intervalle du minuteur est trop long et que la taille de la liste du événement est trop petite, la liste du événement de notification déborde. Pour éviter ce débordement, effectuez l’une des opérations suivantes :

   * Réduisez l&#39;intervalle de temps qui conduit le thread qui effectue l&#39;interrogation des nouveaux événements.
   * Augmentez la taille de la liste de notification.

1. Sérialisez les dernières entrées du événement de notification au format JSON et envoyez les entrées à un serveur distant pour post-traitement.

   Le serveur distant peut alors afficher les données fournies sous forme graphique en temps réel.
1. Pour détecter la perte de événements de notification, recherchez des lacunes dans la séquence de valeurs d’index de événement.

   Chaque événement de notification possède une valeur d&#39;index automatiquement incrémentée par la classe `session.NotificationHistory`.

## Balises ID3 {#id-tags}

Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. TVSDK détecte les balises ID3 au niveau du segment de flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .

>[!IMPORTANT]
>
>TVSDK reconnaît les métadonnées ID3 (version 2.3.0 ou 2.4.0) dans les flux audio (AAC) et vidéo (H.264), dans tous ses encodages possibles (ASCII, UTF8, UTF16-BE ou UTF16-LE). Il ignore les balises ID3 qui ne se trouvent pas dans l’une des versions ou formats reconnus. Le codage non spécifié est traité comme UTF8.

Lorsque TVSDK détecte les métadonnées ID3, il émet une notification contenant les données suivantes :

* InfoCode = 303007
* TYPE = ID3
* NOM = absent
* ID = 0

1. Implémentez un écouteur de événement pour `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` et enregistrez-le avec l&#39;objet `MediaPlayer`.

   TVSDK appelle cet écouteur lorsqu’il détecte les métadonnées ID3.

   >[!NOTE]
   >
   >Les indices publicitaires personnalisés utilisent le même événement `onTimedMetadata` pour indiquer la détection d’une nouvelle balise. Cela ne doit pas entraîner de confusion, car des indices publicitaires personnalisés sont détectés au niveau du manifeste et les balises ID3 sont incorporées dans le flux. Pour plus d’informations, voir custom-tags-configure .

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
