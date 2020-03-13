---
description: Lors de la lecture du contenu, le navigateur TVSDK peut afficher des publicités et transmettre des informations sur les publicités lors de la création de l’objet MediaResource.
seo-description: Lors de la lecture du contenu, le navigateur TVSDK peut afficher des publicités et transmettre des informations sur les publicités lors de la création de l’objet MediaResource.
seo-title: Publicités
title: Publicités
uuid: 9a5e8c83-18ce-41e8-9cb1-fdc9da903faf
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#ads-overview}

Lors de la lecture du contenu, le navigateur TVSDK peut afficher des publicités et transmettre des informations sur les publicités lors de la création de l’objet MediaResource.

Vous pouvez éventuellement appeler la `prepareToPlay` fonction après réception `AdobePSDK.MediaPlayerStatus.INITIALIZED`.

```js
function onStatusChange (event) { 
   switch (event.status) { 
     case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
        player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
        break; 
     case AdobePSDK.MediaPlayerStatus.PREPARED: 
        player.play(); 
        break; 
   } 
} 
 
var auditudeSettings     = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.domain  = "sample_auditude_domain"; 
auditudeSettings.mediaId = "sample_media_id"; 
auditudeSettings.zoneId  = "sample_zone_id"; 
 
// event handler 
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange); 
 
var mediaResource = new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
```

Le kit de développement TVSDK du navigateur fournit également les  de spécifiques aux annonces suivantes que vous pouvez utiliser dans vos gestionnaires de pour empêcher le transfert rapide du contenu lors de la lecture des publicités :

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`
* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

Pour que cela fonctionne dans l’interface utilisateur, spécifiez les paramètres d’annonce dans la configuration comme suit :

```js
// Using UI Framework 
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
        mediaResource: { 
 
            resourceUrl:'Specify Resource Url', 
 
            auditudeSettings: { 
                validMimeTypes: ["application/x-mpeURL"], 
                domain: "Sample_auditude_domain", 
                mediaId:"sample_media_id", 
                zoneID:"sample_zone_id", 
                creativeRepackagingEnabled:true 
            } 
        } 
    } 
}; 
```

Pour plus d’informations sur les métadonnées requises `AuditudeSettings`, voir Métadonnées [d’insertion](../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md)d’annonce.
