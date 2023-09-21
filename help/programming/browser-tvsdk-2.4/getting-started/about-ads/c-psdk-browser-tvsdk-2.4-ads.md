---
description: Lorsque le contenu est en cours de lecture, le TVSDK du navigateur peut afficher des publicités et transmettre des informations sur les publicités lors de la création de l’objet MediaResource .
title: Publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Présentation {#ads-overview}

Lorsque le contenu est en cours de lecture, le TVSDK du navigateur peut afficher des publicités et transmettre des informations sur les publicités lors de la création de l’objet MediaResource .

Vous pouvez éventuellement appeler la fonction `prepareToPlay` fonction après réception `AdobePSDK.MediaPlayerStatus.INITIALIZED`.

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

Le navigateur TVSDK fournit également les événements spécifiques aux publicités suivants que vous pouvez utiliser dans vos gestionnaires d’événements pour empêcher le contenu de se déplacer rapidement lorsque des publicités sont lues :

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

Pour plus d’informations sur les `AuditudeSettings`, voir [Métadonnées d’insertion publicitaire](../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md).
