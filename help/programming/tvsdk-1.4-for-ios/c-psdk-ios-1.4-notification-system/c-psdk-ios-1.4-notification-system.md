---
description: Les objets PTNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
title: Notifications d’état, d’activité, d’erreurs et de journaux du lecteur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Notifications d’état, d’activité, d’erreurs et de journalisation du lecteur  {#notifications-for-player-status-activity-errors-and-logs-overview}

Les objets PTNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.

Votre application peut récupérer les informations de notification et d’état. Vous pouvez également créer un système de journalisation pour les diagnostics et la validation à l’aide des informations de notification.

>[!IMPORTANT]
>
>TVSDK utilise également *`notification`* à ce sujet `NSNotifications` ( `PTMediaPlayer` notifications) *`event`* notifications, distribuées pour fournir des informations sur l’activité du lecteur.

Problèmes également liés à TVSDK `PTMediaPlayerNewNotificationItemEntryNotification` lorsqu’il est problématique ; `PTNotification`.

Vous implémentez des écouteurs d’événements pour capturer les événements et y répondre. De nombreux événements fournissent des `PTNotification` notifications d’état.

## Contenu des notifications {#notification-content}

PTNotification fournit des informations relatives au statut du lecteur.

TVSDK fournit une liste chronologique de `PTNotification` notifications. Chaque notification contient les informations suivantes :

* Horodatage
* Métadonnées de diagnostic composées des éléments suivants :

   * `type`: INFO, AVERTISSEMENT ou ERREUR.
   * `code`: représentation numérique de la notification.
   * `name`: description lisible par l’utilisateur de la notification, telle que SEEK_ERROR
   * `metadata`: paires clé/valeur contenant des informations pertinentes sur la notification. Par exemple, une clé nommée `URL` fournit une valeur qui est une URL liée à la notification.

   * `innerNotification`: référence à une autre `PTNotification` qui impacte directement cette notification.

Vous pouvez stocker ces informations localement pour une analyse ultérieure ou les envoyer à un serveur distant pour la journalisation et la représentation graphique.

## Configuration des notifications {#notification-setup}

TVSDK configure le lecteur pour les notifications de base, bien que vous deviez effectuer la même configuration pour vos notifications personnalisées.

Il existe deux mises en oeuvre pour `PTNotification`:

* Écouter
* Pour ajouter des notifications personnalisées à `PTNotificationHistory`

Pour écouter les notifications, TVSDK instancie la variable `PTNotification` et l’associe à une instance de la fonction `PTMediaPlayerItem`, joint à une instance PTMediaPlayer. Il n&#39;y en a qu&#39;un `PTNotificationHistory` instance par `PTMediaPlayer`.

>[!IMPORTANT]
>
>Si vous ajoutez des personnalisations, vos applications, et non TVSDK, doivent effectuer ces étapes.

## Écoute des notifications {#listen-to-notifications}

Il existe deux façons d’écouter le `PTNotification` dans la `PTMediaPlayer`:

1. Vérifiez manuellement le `PTNotificationHistory` de `PTMediaPlayerItem` avec un minuteur et vérifiez les différences :

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. Utilisez la variable [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) de `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Inscrivez-vous au `NSNotification` en utilisant l’instance de la variable `PTMediaPlayer` à partir duquel vous souhaitez obtenir des notifications :

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Mise en oeuvre des rappels de notification {#implement-notification-callbacks}

Vous pouvez mettre en oeuvre des rappels de notification.

1. Mettez en oeuvre le rappel de notification en obtenant la variable `PTNotification` de la `NSNotification` informations sur l’utilisateur et la lecture de ses valeurs à l’aide de `PTMediaPlayerNotificationKey`:

   ```
   - (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
       PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
       NSLog(@"Notification: %@", notification); 
   }
   ```

## Ajout de notifications personnalisées {#add-custom-notifications}

Pour ajouter une notification personnalisée : créez une `PTNotification` et ajoutez-le à la variable `PTNotificationHistory` en utilisant la variable `PTMediaPlayerItem`:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
