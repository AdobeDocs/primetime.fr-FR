---
description: Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de notification appropriés.
seo-description: Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de notification appropriés.
seo-title: Ajouter des écouteurs pour les notifications de métadonnées minutées
title: Ajouter des écouteurs pour les notifications de métadonnées minutées
uuid: dcd1bd92-0617-4eab-8b06-7301aaff42f3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Ajouter les écouteurs pour les notifications de métadonnées minutées {#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de notification appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant les événements suivants, qui avertissent votre application de l’activité associée :

* `PTTimedMetadataChangedNotification`: Chaque fois qu’une balise d’abonnement unique est identifiée lors de l’analyse du contenu, TVSDK prépare un nouvel  `PTTimedMetadata` objet et envoie cette notification.

   L’objet contient le nom de la balise à laquelle vous vous êtes abonné, l’heure locale de lecture à laquelle cette balise apparaîtra, ainsi que d’autres données.

* `PTMediaPlayerTimeChangeNotification` : Pour les flux en direct/linéaires où le manifeste/la liste de lecture est régulièrement actualisé, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/le manifeste mis à jour, de sorte que  `TimedMetadata` des objets supplémentaires peuvent être ajoutés à la  `MediaPlayerItem.timedMetadata` propriété.

   Ce événement avertit votre application lorsque cela se produit.

   Récupérez les métadonnées minutées de l’une des manières suivantes.

   * Définissez votre application pour qu’elle s’ajoute en tant que processus d’écoute à la notification `PTTimedMetadataChangedNotification` et récupérez l’objet à l’aide de `PTTimedMetadataKey`.

      ```
      [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
        name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
      
      - (void) onTimedMetadataChanged:(NSNotification *) notification { 
          NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
          PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
      }
      ```

   * Accédez à la propriété `timedMetadataCollection` de `PTMediaPlayerItem`, qui comprend tous les objets `PTTimedMetadata` qui ont été notifiés jusqu&#39;à présent.

