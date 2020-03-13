---
description: Les objets PTNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
seo-description: Les objets PTNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
seo-title: Notifications pour l’état du lecteur, le  , les erreurs et les journaux
title: Notifications pour l’état du lecteur, le  , les erreurs et les journaux
uuid: 59716a66-3736-4076-8011-8104bfe3a83a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Notifications pour l’état du lecteur, le  , les erreurs et la journalisation {#notifications-for-player-status-activity-errors-and-logs-overview}

Les objets PTNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.

Votre application peut récupérer la notification et les informations d’état. Vous pouvez également créer un système de journalisation pour les diagnostics et la validation à l’aide des informations de notification.

>[!IMPORTANT]
>
>TVSDK utilise également *`notification`* pour se référer aux `NSNotifications` ( `PTMediaPlayer` notifications) *`event`* notifications, distribuées pour fournir des informations sur le lecteur  .

TVSDK émet également `PTMediaPlayerNewNotificationItemEntryNotification` des problèmes lorsqu’il est publié `PTNotification`.

Vous implémentez des écouteurs  pour capturer et répondre aux  de. De nombreux  fournissent des notifications `PTNotification` d’état.

## Contenu de notification {#notification-content}

PTNotification fournit des informations relatives au statut du lecteur.

TVSDK fournit un chronologique des `PTNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic composées des éléments suivants :

   * `type`: INFORMATIONS, AVERTISSEMENT ou ERREUR.
   * `code`: Représentation numérique de la notification.
   * `name`: Description lisible de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur qui contient des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: Référence à un autre `PTNotification` objet qui affecte directement cette notification.

Vous pouvez stocker ces informations en local pour  plus tard  ou les envoyer à un serveur distant pour la journalisation et la représentation graphique.

## Configuration des notifications {#notification-setup}

TVSDK configure le lecteur pour les notifications de base, bien que vous deviez effectuer la même configuration pour vos notifications personnalisées.

Il existe deux implémentations pour `PTNotification`:

* Pour écouter
* Pour ajouter des notifications personnalisées à `PTNotificationHistory`

Pour écouter les notifications, TVSDK instancie la `PTNotification` classe et l’attache à une instance de la `PTMediaPlayerItem`, qui est jointe à une instance PTMediaPlayer. Il n&#39;y a qu&#39;une seule `PTNotificationHistory` instance par `PTMediaPlayer`.

>[!IMPORTANT]
>
>Si vous ajoutez des personnalisations, vos applications et non TVSDK doivent effectuer ces étapes.

## Écoute des notifications {#listen-to-notifications}

Il existe deux manières d’écouter la `PTNotification` notification dans le `PTMediaPlayer`:

1. Vérifiez manuellement la `PTNotificationHistory` valeur du `PTMediaPlayerItem` minuteur et vérifiez les différences :

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. Utilisez la [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) publiée du `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Enregistrez-vous au `NSNotification` moyen de l’instance de `PTMediaPlayer` laquelle vous souhaitez recevoir des notifications :

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Mise en oeuvre des rappels de notification {#implement-notification-callbacks}

Vous pouvez mettre en oeuvre des rappels de notification.

1. Implémentez le rappel de notification en récupérant les informations `PTNotification` de l’ `NSNotification` utilisateur et en lisant ses valeurs à l’aide `PTMediaPlayerNotificationKey`:

   ```
   - (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
       PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
       NSLog(@"Notification: %@", notification); 
   }
   ```

## Ajouter de notifications personnalisées {#add-custom-notifications}

Pour ajouter une notification personnalisée :
Créez un nouveau fichier `PTNotification` et ajoutez-le au fichier `PTNotificationHistory` à l’aide de l’élément `PTMediaPlayerItem`:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
