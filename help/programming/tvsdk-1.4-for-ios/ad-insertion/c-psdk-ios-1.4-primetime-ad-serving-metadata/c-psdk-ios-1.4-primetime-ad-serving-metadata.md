---
description: TVSDK prend en charge la résolution et l’insertion de publicités pour les flux VOD et direct/linéaire.
title: Métadonnées du serveur de publicités Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Présentation {#primetime-ad-server-metadata-overview}

TVSDK prend en charge la résolution et l’insertion de publicités pour les flux VOD et direct/linéaire.

>[!NOTE]
>
>Avant d’inclure de la publicité dans votre contenu vidéo, fournissez les informations de métadonnées suivantes :
>
>* A `mediaID`, qui identifie le contenu spécifique à lire.
>* Votre `zoneID`, qui identifie votre société ou votre site web.
>* Votre domaine de serveur d’annonces, qui spécifie le domaine de votre serveur d’annonces affecté.
>* Autres paramètres de ciblage.
>

## Configuration des métadonnées du serveur de publicités Primetime {#section_86C4A3B2DF124770B9B7FD2511394313}

Votre application doit fournir TVSDK avec les `PTAuditudeMetadata` informations pour vous connecter au serveur d’annonces.

Pour configurer les métadonnées du serveur d’annonces, procédez comme suit :

1. Création d’une instance de [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) et définissez ses propriétés.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Définissez la variable `PTAuditudeMetadata` instance en tant que métadonnées pour la `PTMediaPlayerItem` métadonnées en utilisant `PTAdResolvingMetadataKey`.

   ```
   // Metadata is an instance of PTMetadata that is used to create the PTMediaPlayerItem 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey];  
   [adMetadata release];
   ```

   Voici un exemple :

   ```
   PTMetadata *metadata = [self createMetadata]; 
   PTMediaPlayerItem *item =  
     [[[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease]; 
   
   - (PTMetadata *) createMetadata { 
       PTMetadata* metadata = [[[PTMetadata alloc] init] autorelease]; 
   
       PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
       adMetadata.zoneId = yourZoneID; 
       adMetadata.domain = yourAdServerDomain; 
   
       [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   
       return metadata; 
   }
   ```

## Activation des publicités lors de la relecture de l’événement complet {#section_6016E1DAF03645C8A8388D03C6AB7571}

La relecture d’événement complet (FER) est une ressource VOD qui agit en tant que ressource de lecture/d’enregistrement numérique (DVR). Votre application doit donc prendre des mesures pour s’assurer que les publicités sont correctement placées.

Pour le contenu en direct, TVSDK utilise les métadonnées/indices du manifeste pour déterminer où placer des publicités. Cependant, il arrive que le contenu en direct/linéaire ressemble au contenu VOD. Par exemple, une `EXT-X-ENDLIST` est ajoutée au manifeste en direct. Pour HLS, la variable `EXT-X-ENDLIST` tag signifie que la diffusion est un flux VOD. TVSDK ne peut pas automatiquement différencier ce flux d’un flux VOD normal pour insérer correctement des publicités.

Votre application doit indiquer à TVSDK si le contenu est actif ou VOD en spécifiant la variable `PTAdSignalingMode`.

Pour un flux FER, le serveur de prise de décision publicitaire Adobe Primetime ne doit pas fournir la liste des coupures publicitaires qui doivent être insérées dans la chronologie avant de démarrer la lecture. Il s’agit du processus type pour le contenu VOD. Au lieu de cela, en spécifiant un mode de signalisation différent, TVSDK lit tous les points de repère du manifeste FER et va au serveur de publicités pour chaque point de repère pour demander une coupure publicitaire. Ce processus est similaire au contenu en direct/DVR.

Outre chaque requête associée à un point de repère, TVSDK effectue une requête de publicité supplémentaire pour les publicités preroll.

1. À partir d’une source externe, telle que vCMS, obtenez le mode de signalisation qui doit être utilisé.
1. Créez les métadonnées liées à la publicité.
1. Si le comportement par défaut doit être remplacé, indiquez la variable `PTAdSignalingMode` en utilisant `PTAdMetadata.signalingMode`.

   Les valeurs valides sont `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues`, et `PTAdSignalingModeServerMap`.

   Vous devez définir le mode de signalisation de la publicité avant d’appeler `prepareToPlay`. Une fois que TVSDK a commencé à résoudre et à placer des publicités dans la chronologie, les modifications apportées au mode de signalisation publicitaire sont ignorées. Définissez le mode lorsque vous créez les métadonnées publicitaires pour la ressource.

1. Passez à la lecture.

   ```
      PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.zoneId = your-auditude-zone-id; 
   adMetadata.domain = @"your-auditude-domain"; 
   //adMetadata.enableDVRAds = YES; // FOR LIVE DVR case 
   //adMetadata.signalingMode = PTAdSignalingModeManifestCues;  
   // FOR VOD FER case 
   NSMutableDictionary *targetingParameters = [[[NSMutableDictionary alloc] init] autorelease]; 
   [targetingParameters setValue:@"ipad" forKey:@"device"]; 
   [targetingParameters setValue:@"preroll" forKey:@"AD_OPPORTUNITY_ID"]; 
   adMetadata.targetingParameters = targetingParameters; 
   NSMutableDictionary *customParameters = [[[NSMutableDictionary alloc] init] autorelease]; 
   [customParameters setValue:@"your-media-id" forKey:@"NW_ID"]; 
   [customParameters setValue:@"preroll" forKey:@"AD_OPPORTUNITY_ID"]; 
   adMetadata.customParameters = customParameters; 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   ```
