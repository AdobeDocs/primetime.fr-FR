---
description: Pour recevoir des notifications sur les balises dans le manifeste, vous devez mettre en oeuvre les écouteurs  appropriés.
seo-description: Pour recevoir des notifications sur les balises dans le manifeste, vous devez mettre en oeuvre les écouteurs  appropriés.
seo-title: Ajouter des écouteurs pour les notifications de métadonnées minutées
title: Ajouter des écouteurs pour les notifications de métadonnées minutées
uuid: bb996b4a-282e-4321-a9e9-513f0df45b70
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Ajouter des écouteurs pour les notifications de métadonnées minutées {#add-listeners-for-timed-metadata-notifications}

Pour recevoir des notifications sur les balises dans le manifeste, vous devez mettre en oeuvre les écouteurs  appropriés.

Vous pouvez surveiller les métadonnées minutées en écoutant `onTimedMetadata`, qui avertissent votre application des   connexes. Chaque fois qu’une balise abonnée unique est identifiée lors de l’analyse du contenu, TVSDK prépare un nouvel `TimedMetadata` objet et distribue ce . L’objet contient le nom de la balise à laquelle vous vous êtes abonné, l’heure locale de la lecture où cette balise apparaîtra, ainsi que d’autres données.

Écoute les .

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

Les métadonnées ID3 utilisent le même `onTimedMetadata` écouteur pour indiquer la présence d’une balise ID3. Cela ne doit toutefois pas créer de confusion, car vous pouvez utiliser la `TimedMetadata` propriété `type` pour différencier TAG et ID3. Pour plus d’informations sur les balises ID3, voir Balises [ID3](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-id3-metadata-retrieve.md).