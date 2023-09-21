---
description: Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de notification appropriés.
title: Ajout d’écouteurs pour les notifications de métadonnées minutées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Ajout d’écouteurs pour les notifications de métadonnées minutées {#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de notification appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant les événements suivants, qui notifient votre application de l’activité associée :

* `PTTimedMetadataChangedNotification`: à chaque fois qu’une balise d’abonnement unique est identifiée lors de l’analyse du contenu, TVSDK prépare une nouvelle `PTTimedMetadata` et envoie cette notification.

  L’objet contient le nom de la balise à laquelle vous vous êtes abonné, l’heure locale de la lecture à laquelle cette balise apparaîtra, ainsi que d’autres données.

* `PTMediaPlayerTimeChangeNotification` : pour les flux en direct/linéaires où la liste de lecture/manifeste s’actualise régulièrement, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/manifeste mise à jour, donc des balises supplémentaires `TimedMetadata` peut être ajouté à la variable `MediaPlayerItem.timedMetadata` .

  Cet événement avertit votre application lorsque cela se produit.

  Récupérez les métadonnées minutées de l’une des manières suivantes.

   * Définissez votre application pour qu’elle s’ajoute en tant qu’écouteur à la variable `PTTimedMetadataChangedNotification` notification et récupération de l’objet à l’aide de `PTTimedMetadataKey`.

     ```
     [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
       name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
     
     - (void) onTimedMetadataChanged:(NSNotification *) notification { 
         NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
         PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
     }
     ```

   * Accédez au `timedMetadataCollection` de `PTMediaPlayerItem`, qui comprend tous les `PTTimedMetadata` des objets qui ont été notifiés jusqu’à présent.
