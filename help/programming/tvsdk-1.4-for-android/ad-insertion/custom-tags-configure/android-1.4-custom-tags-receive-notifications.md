---
description: Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de événement appropriés.
title: Ajouter des écouteurs pour les notifications de métadonnées minutées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# Ajouter les écouteurs pour les notifications de métadonnées minutées {#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur les balises dans le manifeste, implémentez le ou les écouteurs de événement appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant les événements suivants, qui avertissent votre application de l’activité associée :

* `onTimedMetadata`: Chaque fois qu’une balise d’abonnement unique est identifiée lors de l’analyse du contenu, TVSDK prépare un nouvel  `TimedMetadata` objet et distribue ce événement.

   L’objet contient le nom de la balise à laquelle vous vous êtes abonné, l’heure locale de lecture à laquelle cette balise apparaîtra, ainsi que d’autres données.

   Écoute les événements.

   ```java
   private final TimedMetadataEventListener timedMetadataEventListener =  
     new TimedMetadataEventListener() { 
       @Override 
       public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { 
           TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata(); 
   
           TimedMetadata.Type type = timedMetadata.getType(); 
           if (type.equals(TimedMetadata.Type.ID3)){ 
               Metadata metadata = timedMetadata.getMetadata(); 
               Set<String> keys = metadata.keySet(); 
               for (String key : keys) { 
                   String value = metadata.getValue(key); 
               } 
           } else if (_mediaPlayer.getPlaybackRange() !=  
                      null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
               displayRanges(); 
           } 
       } 
   }; 
   ```

Les métadonnées ID3 utilisent le même écouteur onTimedMetadata pour indiquer la présence d’une balise ID3. Cela ne doit toutefois pas prêter à confusion, car vous pouvez utiliser la propriété `type` d&#39;un objet `TimedMetadata` pour différencier la balise TAG de l&#39;ID3. Pour plus d’informations sur les balises ID3, voir [balises ID3](../../../tvsdk-1.4-for-android/notification-system/android-1.4-id3-metadata-retrieve.md).
