---
description: TVSDK prend en charge la résolution et l’insertion de publicités pour les flux VOD et direct/linéaire.
title: Métadonnées du serveur de publicités Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Présentation {#primetime-ad-server-metadata-overview}

TVSDK prend en charge la résolution et l’insertion de publicités pour les flux VOD et direct/linéaire.

## Condition requise

Avant d’inclure de la publicité dans votre contenu vidéo, fournissez les informations de métadonnées suivantes :

* A `mediaID`, qui identifie le contenu spécifique à lire.
* Votre `zoneID`, qui identifie votre société ou votre site web.
* Votre domaine de serveur d’annonces, qui spécifie le domaine de votre serveur d’annonces affecté.
* Autres paramètres de ciblage.

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
