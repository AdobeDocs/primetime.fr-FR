---
description: Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de notification appropriés.
seo-description: Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de notification appropriés.
seo-title: Ajouter des écouteurs pour les notifications de métadonnées minutées
title: Ajouter des écouteurs pour les notifications de métadonnées minutées
uuid: dcd1bd92-0617-4eab-8b06-7301aaff42f3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Ajouter des écouteurs pour les notifications de métadonnées minutées {#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de notification appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant les  de suivantes, qui avertissent votre application des  de connexes :

* `PTTimedMetadataChangedNotification`: Chaque fois qu’une balise abonnée unique est identifiée lors de l’analyse du contenu, TVSDK prépare un nouvel `PTTimedMetadata` objet et envoie cette notification.

   L’objet contient le nom de la balise à laquelle vous vous êtes abonné, l’heure locale de la lecture où cette balise apparaîtra, ainsi que d’autres données.

* `PTMediaPlayerTimeChangeNotification` : Dans le cas des flux en direct/linéaires dans lesquels le manifeste/la liste de lecture est régulièrement actualisé, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/le manifeste mis à jour. Des `TimedMetadata` objets supplémentaires peuvent donc être ajoutés à la `MediaPlayerItem.timedMetadata` propriété.

   Ce avertit votre application lorsque cela se produit.

   Récupérez les métadonnées minutées de l’une des manières suivantes.

   * Définissez votre application pour qu’elle s’ajoute en tant qu’écouteur à la `PTTimedMetadataChangedNotification` notification et récupérez l’objet à l’aide `PTTimedMetadataKey`.

      ```
      [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
        name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
      
      - (void) onTimedMetadataChanged:(NSNotification *) notification { 
          NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
          PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
      }
      ```

   * Accédez à la `timedMetadataCollection` propriété de `PTMediaPlayerItem`, qui comprend tous les `PTTimedMetadata` objets qui ont été notifiés jusqu’à présent.

