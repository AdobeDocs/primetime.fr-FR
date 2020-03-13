---
description: Vous pouvez décider de résoudre uniquement les publicités qui surviennent après le point de production actuel de l’utilisateur ou également les publicités qui surviennent avant le point de production actuel.
seo-description: Vous pouvez décider de résoudre uniquement les publicités qui surviennent après le point de production actuel de l’utilisateur ou également les publicités qui surviennent avant le point de production actuel.
seo-title: Charger une publicité pour une fenêtre DVR
title: Charger une publicité pour une fenêtre DVR
uuid: 67bc3924-3d17-4d1a-b9a7-be8d0488a970
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Charger une publicité pour une fenêtre DVR {#load-ad-for-a-dvr-window}

Vous pouvez décider de résoudre uniquement les publicités qui surviennent après le point de production actuel de l’utilisateur ou également les publicités qui surviennent avant le point de production actuel.

Lorsqu’un utilisateur  de de contenu  au début d’un flux DVR, TVSDK résout toutes les publicités du flux à ce moment-là. Toutefois, lorsque l’utilisateur  de  le contenu à un moment situé après le début du flux, vous pouvez décider de résoudre uniquement les publicités qui surviennent après le point de diffusion actif de l’utilisateur ou également les publicités qui se sont produites avant le point de diffusion actif.

>[!TIP]
>
>Il est plus rapide de résoudre les publicités après le point de diffusion actuel, mais si l’utilisateur effectue une recherche en amont, cette option empêche le lecteur de lire les publicités qui s’affichaient précédemment.

## Contrôle et chargement d’une fenêtre DVR {#section_2D93E2E947644D66B6F6ED1DD6742C25}

Pour contrôler le chargement d&#39;une fenêtre DVR:

Pour charger toutes les publicités pour l’ensemble du flux, définissez la `PTAdMetadata.enableDVRAds` propriété sur `YES`.

>[!NOTE]
>
>La valeur par défaut est `NO`, et cette option charge uniquement les publicités à partir du point de production actuel.

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
