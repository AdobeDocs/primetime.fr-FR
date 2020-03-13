---
description: TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.
seo-description: TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.
seo-title: Métadonnées du serveur Primetime
title: Métadonnées du serveur Primetime
uuid: 61e224dd-551a-438f-8560-e64915087fef
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Activer les publicités en  de lecture en plein {#section_6016E1DAF03645C8A8388D03C6AB7571}

La relecture de  en mode plein (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre les mesures nécessaires pour s’assurer que les publicités sont correctement placées.

Pour le contenu en direct, TVSDK utilise les métadonnées/indices du manifeste pour déterminer l’emplacement des publicités. Cependant, il arrive que le contenu dynamique/linéaire ressemble au contenu VOD. Par exemple, lorsque le contenu en direct se termine, une `EXT-X-ENDLIST` balise est ajoutée au manifeste en direct. Pour HLS, la `EXT-X-ENDLIST` balise signifie que le flux est un flux VOD. TVSDK ne peut pas automatiquement différencier ce flux d’un flux VOD normal pour insérer correctement des publicités.

Votre application doit indiquer à TVSDK si le contenu est en direct ou VOD en spécifiant le `PTAdSignalingMode`.

Dans le cas d’un flux FER, le serveur Adobe Primetime de prise de décision publicitaire ne doit pas fournir le de coupures publicitaires à insérer dans la chronologie avant de commencer la lecture. Il s’agit du processus typique pour le contenu VOD. Au lieu de cela, en spécifiant un mode de signalisation différent, TVSDK lit tous les points de repère du manifeste FER et va au serveur d’annonces pour chaque point de repère pour demander une coupure publicitaire. Ce processus est similaire au contenu en direct/DVR.

Outre chaque requête associée à un point de repère, TVSDK effectue une demande de publicité supplémentaire pour les publicités preroll.

1. A partir d’une source externe, telle que vCMS, obtenez le mode de signalisation à utiliser.
1. Créez les métadonnées liées à la publicité.
1. Si le comportement par défaut doit être remplacé, spécifiez le comportement `PTAdSignalingMode` en utilisant `PTAdMetadata.signalingMode`.

   Les valeurs valides sont `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues`et `PTAdSignalingModeServerMap`.

   Vous devez définir le mode de signalisation de la publicité avant d’appeler `prepareToPlay`. Une fois que le TVSDK a résolu et placé les publicités dans le plan de montage chronologique, les modifications apportées au mode de signalisation publicitaire sont ignorées. Définissez le mode lorsque vous créez les métadonnées publicitaires pour la ressource.

1. Poursuivez la lecture.

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
