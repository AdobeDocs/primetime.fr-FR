---
description: Pour recevoir des notifications sur les balises dans le manifeste, vous devez mettre en oeuvre les écouteurs de événement appropriés.
seo-description: Pour recevoir des notifications sur les balises dans le manifeste, vous devez mettre en oeuvre les écouteurs de événement appropriés.
seo-title: Ajouter écouteurs pour les notifications de métadonnées minutées
title: Ajouter écouteurs pour les notifications de métadonnées minutées
uuid: 336882e7-e2d8-49b8-a23d-f236c7e6a594
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Ajouter écouteurs pour les notifications de métadonnées minutées {#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur les balises dans le manifeste, vous devez mettre en oeuvre les écouteurs de événement appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant `onTimedMetadata`les données, qui signalent à votre application l’activité associée. Chaque fois qu’une balise d’abonnement unique est identifiée lors de l’analyse du contenu, TVSDK prépare un nouvel `TimedMetadata` objet et distribue ce événement. L’objet contient le nom de la balise à laquelle vous vous êtes abonné, l’heure locale de lecture à laquelle cette balise apparaîtra, ainsi que d’autres données.

1. Écoute les événements.

   ```java
   private final TimedMetadataEventListener timedMetadataEventListener = new TimedMetadataEventListener() { 
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
           } else if (_mediaPlayer.getPlaybackRange() != null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
               displayRanges(); 
           } 
       } 
   }; 
   ```

Les métadonnées ID3 utilisent le même `onTimedMetadata` processus d’écoute pour indiquer la présence d’une balise ID3. Cela ne doit toutefois pas prêter à confusion, car vous pouvez utiliser la `TimedMetadata``type` propriété pour différencier TAG et ID3. Pour plus d’informations sur les balises ID3, voir Balises [](../../content-playback-options/t-psdk-android-2.7-id3-metadata-retrieve.md)ID3.