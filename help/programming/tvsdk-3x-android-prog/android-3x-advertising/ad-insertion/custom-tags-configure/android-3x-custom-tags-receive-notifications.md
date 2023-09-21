---
description: Pour recevoir des notifications sur les balises dans le manifeste, vous devez mettre en oeuvre les écouteurs d’événement appropriés.
title: Ajout d’écouteurs pour les notifications de métadonnées minutées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Ajout d’écouteurs pour les notifications de métadonnées minutées {#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur les balises dans le manifeste, vous devez mettre en oeuvre les écouteurs d’événement appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant les `onTimedMetadata`, qui notifient l’application de l’activité associée. Chaque fois qu’une balise d’abonnement unique est identifiée lors de l’analyse du contenu, TVSDK prépare une nouvelle `TimedMetadata` et distribue cet événement. L’objet contient le nom de la balise à laquelle vous vous êtes abonné, l’heure locale de la lecture à laquelle cette balise apparaîtra, ainsi que d’autres données.

Prêtez attention aux événements.

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

Les métadonnées ID3 utilisent le même `onTimedMetadata` écouteur pour indiquer la présence d’une balise ID3. Cela ne doit toutefois pas prêter à confusion, car vous pouvez utiliser la variable `TimedMetadata` `type` pour différencier TAG et ID3. Pour plus d’informations sur les balises ID3, voir [Balises ID3](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-id3-metadata-retrieve.md).
