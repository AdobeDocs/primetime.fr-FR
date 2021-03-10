---
description: TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.
title: Métadonnées du serveur et de l’heure de priorité
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Aperçu {#primetime-ad-server-metadata-overview}

TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.

## Condition préalable

Avant d’inclure de la publicité dans votre contenu vidéo, fournissez les métadonnées suivantes :

* `mediaID`, qui identifie le contenu spécifique à lire.
* Votre `zoneID`, qui identifie votre société ou votre site Web.
* Le domaine de votre serveur d’annonces, qui spécifie le domaine de votre serveur d’annonces affecté.
* Autres paramètres de ciblage.

## Configurer les métadonnées de serveur et Primetime {#section_86C4A3B2DF124770B9B7FD2511394313}

Votre application doit fournir à TVSDK les informations `PTAuditudeMetadata` requises pour se connecter au serveur d’annonces.

Pour configurer les métadonnées du serveur d’annonces :

1. Créez une instance de [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) et définissez ses propriétés.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Définissez l&#39;instance `PTAuditudeMetadata` comme métadonnées pour les métadonnées `PTMediaPlayerItem` actuelles à l&#39;aide de `PTAdResolvingMetadataKey`.

   ```
   // Metadata is an instance of PTMetadata that is used to create the PTMediaPlayerItem 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey];  
   [adMetadata release];
   ```

   En voici un exemple :

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
