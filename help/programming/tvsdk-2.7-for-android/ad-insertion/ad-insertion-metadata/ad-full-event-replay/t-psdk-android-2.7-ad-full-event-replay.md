---
description: La relecture d’événement complet (FER) est une ressource VOD qui agit en tant que ressource de lecture/d’enregistrement numérique (DVR). Votre application doit donc prendre des mesures pour s’assurer que les publicités sont correctement placées.
title: Activation des publicités lors de la relecture de l’événement complet
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Activation des publicités lors de la relecture de l’événement complet {#enable-ads-in-full-event-replay-overview}

La relecture d’événement complet (FER) est une ressource VOD qui agit en tant que ressource de lecture/d’enregistrement numérique (DVR). Votre application doit donc prendre des mesures pour s’assurer que les publicités sont correctement placées.

Pour le contenu en direct, TVSDK utilise les métadonnées/indices du manifeste pour déterminer où placer des publicités. Cependant, il arrive que le contenu en direct/linéaire ressemble au contenu VOD. Par exemple, une `EXT-X-ENDLIST` est ajoutée au manifeste en direct. Pour HLS, la variable `EXT-X-ENDLIST` tag signifie que la diffusion est un flux VOD. Pour insérer correctement des publicités, TVSDK ne peut pas automatiquement différencier ce flux d’un flux VOD type.

Votre application doit indiquer à TVSDK si le contenu est actif ou VOD en spécifiant la variable `AdSignalingMode`.

Pour un flux FER, le serveur de prise de décision publicitaire Adobe Primetime ne doit pas fournir la liste des coupures publicitaires qui doivent être insérées dans la chronologie avant de démarrer la lecture. Il s’agit du processus type pour le contenu VOD. Au lieu de cela, en spécifiant un mode de signalisation différent, TVSDK lit tous les points de repère du manifeste FER et va au serveur de publicités pour chaque point de repère pour demander une coupure publicitaire. Ce processus est similaire au contenu en direct/DVR.

>[!TIP]
>
>Outre chaque requête associée à un point de repère, TVSDK effectue une requête de publicité supplémentaire pour les publicités preroll.

1. À partir d’une source externe, telle que vCMS, obtenez le mode de signalisation qui doit être utilisé.
1. Créez les métadonnées liées à la publicité.
1. Si le comportement par défaut doit être remplacé, indiquez la variable `AdSignalingMode` en utilisant `AdvertisingMetadata.setSignalingMode`.

   Les valeurs valides sont `DEFAULT`, `SERVER_MAP`, et `MANIFEST_CUES`.

   >[!IMPORTANT]
   >
   >Vous devez définir le mode de signalisation de la publicité avant d’appeler `prepareToPlay`. Une fois que TVSDK a commencé à résoudre et à placer des publicités dans la chronologie, les modifications apportées au mode de signalisation publicitaire sont ignorées. Définissez le mode lorsque vous créez le `AuditudeSettings` .

1. Passez à la lecture.

<!--<a id="example_6DECA71C3C3B4551805C09A80686552F"></a>-->

```java
MediaPlayer mediaPlayer =  
  new MediaPlayer(getActivity.().getApplicationContext()); 
 
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings.setSignalingMode(AdSignalingMode.MANIFEST_CUES); 
auditudeSettings.setDomain("your-auditude-domain"); 
auditudeSettings.setZoneId("your-auditude-zone-id"); 
auditudeSettings.setMediaId("your-media-id"); 
// set additional targeting parameters or custom parameters 
 
MediaPlayerItemConfig itemConfig =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
MediaResource mediaResource =  
  new MediaResource("https://example.com/media/test_media.m3u8",  
                    MediaResource.Type.HLS, Metadata); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (status == MediaPlayerStatus.INITIALIZED) { 
            mediaPlayer.prepareToPlay(); 
        } 
        else if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
            // TVSDK is in the PREPARED state, so start the playback 
            mediaPlayer.play(); 
        } 
        else if( event.getStatus() == MediaPlayerStatus.COMPLETE ) { 
            // playback has reached the end of stream ( ads included ) 
            // if we want to rewind we can call 
            mediaPlayer.seek(mediaPlayer.getSeekableRange().getBegin()); 
        } 
    } 
}); 
 
mediaPlayer.replaceCurrentResource(mediaResource, itemConfig); 
```
