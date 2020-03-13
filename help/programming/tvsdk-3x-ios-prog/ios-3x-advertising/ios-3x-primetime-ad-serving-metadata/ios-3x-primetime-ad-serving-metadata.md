---
description: TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.
seo-description: TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.
seo-title: Métadonnées du serveur Primetime
title: Métadonnées du serveur Primetime
uuid: 61e224dd-551a-438f-8560-e64915087fef
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Présentation {#primetime-ad-server-metadata-overview}

TVSDK prend en charge la résolution et l’insertion de publicités pour VOD et les flux vidéo/linéaires.

[!PREREQUISITE] {othertype=&quot;Prérequis&quot;}

Avant d’inclure de la publicité dans votre contenu vidéo, fournissez les informations de métadonnées suivantes :

* Une `mediaID`, qui identifie le contenu spécifique à lire.
* Votre `zoneID`, qui identifie votre ou votre site Web.
* Le domaine du serveur d’annonces, qui spécifie le domaine du serveur d’annonces affecté.
* Autres paramètres de ciblage.

## Configuration des métadonnées de serveur et de Primetime {#section_86C4A3B2DF124770B9B7FD2511394313}

Votre application doit fournir au SDK TVSDK les `PTAuditudeMetadata` informations requises pour la connexion au serveur d’annonces.

Pour configurer les métadonnées du serveur d’annonces :

1. Créez une instance de [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) et définissez ses propriétés.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Définissez l’ `PTAuditudeMetadata` instance en tant que métadonnées pour les `PTMediaPlayerItem` métadonnées actives à l’aide `PTAdResolvingMetadataKey`.

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
