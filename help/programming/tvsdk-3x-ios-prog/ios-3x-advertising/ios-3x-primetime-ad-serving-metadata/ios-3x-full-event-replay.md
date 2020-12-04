---
description: TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.
seo-description: TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.
seo-title: Métadonnées du serveur et de l’heure de priorité
title: Métadonnées du serveur et de l’heure de priorité
uuid: 61e224dd-551a-438f-8560-e64915087fef
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# Activer les publicités dans la relecture en événement complet {#section_6016E1DAF03645C8A8388D03C6AB7571}

La relecture en événement complet (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre des mesures pour s’assurer que les publicités sont placées correctement.

Pour le contenu en direct, TVSDK utilise les métadonnées/indices du manifeste pour déterminer l’emplacement des publicités. Cependant, il arrive que le contenu en direct/linéaire ressemble au contenu VOD. Par exemple, lorsque le contenu en direct se termine, une balise `EXT-X-ENDLIST` est ajoutée au manifeste en direct. Pour HLS, la balise `EXT-X-ENDLIST` signifie que le flux est un flux VOD. TVSDK ne peut pas automatiquement différencier ce flux d’un flux VOD normal pour insérer correctement des publicités.

Votre application doit indiquer à TVSDK si le contenu est actif ou VOD en spécifiant `PTAdSignalingMode`.

Dans le cas d’un flux FER, le serveur de prise de décision publicitaire Adobe Primetime ne doit pas fournir la liste des coupures publicitaires qui doivent être insérées dans la chronologie avant de commencer la lecture. Il s’agit du processus typique pour le contenu VOD. Au lieu de cela, en spécifiant un mode de signalisation différent, TVSDK lit tous les indices du manifeste FER et va au serveur d’annonces pour chaque indice pour demander une coupure publicitaire. Ce processus est similaire au contenu en direct/DVR.

Outre chaque demande associée à un point de repère, TVSDK effectue une demande de publicité supplémentaire pour les publicités preroll.

1. A partir d’une source externe, telle que vCMS, obtenez le mode de signalisation à utiliser.
1. Créez les métadonnées liées à la publicité.
1. Si le comportement par défaut doit être remplacé, spécifiez `PTAdSignalingMode` en utilisant `PTAdMetadata.signalingMode`.

   Les valeurs valides sont `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues` et `PTAdSignalingModeServerMap`.

   Vous devez définir le mode de signalisation de la publicité avant d&#39;appeler `prepareToPlay`. Après les débuts TVSDK de résolution et de placement des publicités dans la chronologie, les modifications apportées au mode de signalisation publicitaire sont ignorées. Définissez le mode lorsque vous créez les métadonnées publicitaires pour la ressource.

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
