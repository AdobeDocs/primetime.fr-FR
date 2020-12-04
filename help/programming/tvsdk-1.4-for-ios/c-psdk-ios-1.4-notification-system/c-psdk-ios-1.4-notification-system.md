---
description: Les objets PTNotification fournissent des informations sur les changements d'état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo modifient également l’état du lecteur.
seo-description: Les objets PTNotification fournissent des informations sur les changements d'état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo modifient également l’état du lecteur.
seo-title: Notifications d’état, d’activité, d’erreurs et de journaux du lecteur
title: Notifications d’état, d’activité, d’erreurs et de journaux du lecteur
uuid: 59716a66-3736-4076-8011-8104bfe3a83a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---


# Notifications d’état du lecteur, d’activité, d’erreurs et de consignation {#notifications-for-player-status-activity-errors-and-logs-overview}

Les objets PTNotification fournissent des informations sur les changements d&#39;état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo modifient également l’état du lecteur.

Votre application peut récupérer la notification et les informations d’état. Vous pouvez également créer un système de journalisation pour les diagnostics et la validation à l’aide des informations de notification.

>[!IMPORTANT]
>
>TVSDK utilise également *`notification`* pour faire référence à `NSNotifications` ( `PTMediaPlayer` notifications) *`event`* notifications, envoyées pour fournir des informations sur l’activité du lecteur.

TVSDK émet également `PTMediaPlayerNewNotificationItemEntryNotification` lorsqu&#39;il émet `PTNotification`.

Vous implémentez des écouteurs de événement pour capturer les événements et y répondre. De nombreux événements fournissent des notifications d’état `PTNotification`.

## Contenu de la notification {#notification-content}

PTNotification fournit des informations relatives au statut du lecteur.

TVSDK fournit une liste chronologique de `PTNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic comprenant les éléments suivants :

   * `type`: INFORMATIONS, AVERTISSEMENT ou ERREUR.
   * `code`: Représentation numérique de la notification.
   * `name`: Description lisible de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur qui contient des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: Référence à un autre  `PTNotification` objet qui a un impact direct sur cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour consigner et représenter graphiquement.

## Configuration de la notification {#notification-setup}

TVSDK installe le lecteur pour les notifications de base, bien que vous deviez effectuer la même configuration pour vos notifications personnalisées.

Il existe deux implémentations pour `PTNotification` :

* Pour écouter
* Pour ajouter des notifications personnalisées à `PTNotificationHistory`

Pour écouter les notifications, TVSDK instancie la classe `PTNotification` et l’attache à une instance de `PTMediaPlayerItem`, qui est jointe à une instance PTMediaPlayer. Il n&#39;y a qu&#39;une seule instance `PTNotificationHistory` par `PTMediaPlayer`.

>[!IMPORTANT]
>
>Si vous ajoutez des personnalisations, vos applications et non TVSDK doivent effectuer ces étapes.

## Écoute des notifications {#listen-to-notifications}

Il existe deux façons d&#39;écouter la notification `PTNotification` dans `PTMediaPlayer` :

1. Vérifiez manuellement le `PTNotificationHistory` de `PTMediaPlayerItem` à l&#39;aide d&#39;un minuteur et vérifiez les différences :

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. Utilisez la [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) publiée du `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Enregistrez-vous au `NSNotification` en utilisant l&#39;instance de `PTMediaPlayer` à partir de laquelle vous souhaitez recevoir des notifications :

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Mise en oeuvre des rappels de notification {#implement-notification-callbacks}

Vous pouvez mettre en oeuvre des rappels de notification.

1. Implémentez le rappel de notification en récupérant `PTNotification` des informations utilisateur `NSNotification` et en lisant ses valeurs à l&#39;aide de `PTMediaPlayerNotificationKey` :

   ```
   - (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
       PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
       NSLog(@"Notification: %@", notification); 
   }
   ```

## Ajouter des notifications personnalisées {#add-custom-notifications}

Pour ajouter une notification personnalisée :
Créez un `PTNotification` et ajoutez-le à `PTNotificationHistory` en utilisant l&#39;élément `PTMediaPlayerItem` actuel :

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
