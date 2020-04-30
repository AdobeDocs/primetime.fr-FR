---
description: La relecture en événement complet (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre des mesures pour s’assurer que les publicités sont placées correctement.
seo-description: La relecture en événement complet (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre des mesures pour s’assurer que les publicités sont placées correctement.
seo-title: Activer les publicités en lecture événement complet
title: Activer les publicités en lecture événement complet
uuid: 69244069-ef61-42e4-b2f5-62ae2561d9e1
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Activer les publicités en lecture événement complet {#enable-ads-in-full-event-replay-overview}

La relecture en événement complet (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre des mesures pour s’assurer que les publicités sont placées correctement.

Pour le contenu en direct, TVSDK utilise les métadonnées/indices du manifeste pour déterminer l’emplacement des publicités. Cependant, il arrive que le contenu en direct/linéaire ressemble au contenu VOD. Par exemple, lorsque le contenu en direct se termine, une `EXT-X-ENDLIST` balise est ajoutée au manifeste en direct. Pour HLS, la `EXT-X-ENDLIST` balise signifie que le flux est un flux VOD. Pour insérer correctement des publicités, TVSDK ne peut pas automatiquement différencier ce flux d’un flux VOD standard.

Votre application doit indiquer à TVSDK si le contenu est actif ou VOD en spécifiant le `AdSignalingMode`.

Dans le cas d’un flux FER, le serveur de prise de décision publicitaire Adobe Primetime ne doit pas fournir la liste des coupures publicitaires qui doivent être insérées dans la chronologie avant de commencer la lecture. Il s’agit du processus typique pour le contenu VOD. Au lieu de cela, en spécifiant un mode de signalisation différent, TVSDK lit tous les indices du manifeste FER et va au serveur d’annonces pour chaque indice pour demander une coupure publicitaire. Ce processus est similaire au contenu en direct/DVR.

>[!TIP]
>
>Outre chaque demande associée à un point de repère, TVSDK effectue une demande de publicité supplémentaire pour les publicités preroll.

1. A partir d’une source externe, telle que vCMS, obtenez le mode de signalisation à utiliser.
1. Créez les métadonnées liées à la publicité.
1. Si le comportement par défaut doit être remplacé, spécifiez le comportement `AdSignalingMode` en utilisant `AdvertisingMetadata.setSignalingMode`.

   Les valeurs valides sont `DEFAULT`, `SERVER_MAP`et `MANIFEST_CUES`.

   >[!IMPORTANT]
   >
   >Vous devez définir le mode de signalisation de la publicité avant d&#39;appeler `prepareToPlay`. Après les débuts TVSDK de résolution et de placement des publicités dans la chronologie, les modifications apportées au mode de signalisation publicitaire sont ignorées. Définissez le mode lorsque vous créez l’ `AuditudeSettings` objet.

1. Poursuivez la lecture.

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
