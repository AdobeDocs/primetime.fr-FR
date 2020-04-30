---
description: Vous pouvez décider de résoudre uniquement les publicités qui surviennent après le point d’activation actuel de l’utilisateur ou également les publicités qui surviennent avant le point d’activation actuel.
seo-description: Vous pouvez décider de résoudre uniquement les publicités qui surviennent après le point d’activation actuel de l’utilisateur ou également les publicités qui surviennent avant le point d’activation actuel.
seo-title: Charger la publicité pour une fenêtre DVR
title: Charger la publicité pour une fenêtre DVR
uuid: 3ae1fbf6-deae-4f39-a17d-43d1fe3cb975
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Charger la publicité pour une fenêtre DVR {#load-ad-for-a-dvr-window}

Vous pouvez décider de résoudre uniquement les publicités qui surviennent après le point d’activation actuel de l’utilisateur ou également les publicités qui surviennent avant le point d’activation actuel.

Lorsqu’un utilisateur début le contenu de la vue au début d’un flux d’enregistrement vidéo numérique, TVSDK résout toutes les publicités du flux à ce moment-là. Cependant, lorsque l’utilisateur début de vue du contenu à un moment situé après le début du flux, vous pouvez décider de résoudre uniquement les publicités qui surviennent après le point de diffusion actif de l’utilisateur ou de résoudre également les publicités qui se sont produites avant le point de diffusion actif.

>[!TIP]
>
>Il est plus rapide de résoudre les publicités une fois le point d’accès actif, mais si l’utilisateur effectue une recherche en amont, cette option empêche le lecteur de lire les publicités qui s’affichaient plus tôt.

## Contrôler le chargement des publicités pour une fenêtre DVR {#section_2D93E2E947644D66B6F6ED1DD6742C25}

Pour contrôler le chargement des publicités pour une fenêtre DVR :

    Pour charger toutes les publicités pour l’ensemble du flux, définissez la propriété &quot;PTAdMetadata.enableDVRAds&quot; sur &quot;YES&quot;.

>[!NOTE]
>
>La valeur par défaut est `NO`définie et cette option charge les publicités uniquement à partir du point d’activation actuel.

Par exemple :

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
 
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
adMetadata.zoneId = <ZoneId>; 
adMetadata.domain = <Domain>; 
 
// Enable DVR Ads by setting to YES the enableDVRAds property on PTAdMetadata  
// (PTAuditudeMetadata is a subclass of PTAdMetadata)  
adMetadata.enableDVRAds = YES; 
 
[metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
 
//Create PTMediaPlayerItem with the previously prepared metadata    
playerItem = [[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata]; 
```
