---
description: Vous pouvez décider de ne résoudre que les publicités qui surviennent après le point d’activation actuel de l’utilisateur ou de résoudre également les publicités qui surviennent avant le point d’activation actuel.
title: Chargement de la publicité pour une fenêtre DVR
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Chargement de la publicité pour une fenêtre DVR {#load-ad-for-a-dvr-window}

Vous pouvez décider de ne résoudre que les publicités qui surviennent après le point d’activation actuel de l’utilisateur ou de résoudre également les publicités qui surviennent avant le point d’activation actuel.

Lorsqu’un utilisateur commence à afficher du contenu au début d’un flux de diffusion numérique (DVR), TVSDK résout toutes les publicités du flux à ce moment-là. Cependant, lorsque l’utilisateur commence à afficher le contenu à un moment après le début de la diffusion, vous pouvez décider de résoudre uniquement les publicités qui se produisent après le point d’activation actuel de l’utilisateur ou de résoudre également les publicités qui se sont produites avant le point d’activation actuel.

>[!TIP]
>
>La résolution des publicités après le point d’activation actuel est plus rapide, mais si l’utilisateur effectue une recherche vers l’arrière, cette option empêche le lecteur de lire les publicités apparues précédemment.

## Contrôler le chargement des publicités pour une fenêtre DVR {#section_2D93E2E947644D66B6F6ED1DD6742C25}

Pour contrôler le chargement des publicités pour une fenêtre DVR :

Pour charger toutes les publicités pour la diffusion entière, définissez la variable `PTAdMetadata.enableDVRAds` de `YES`.

>[!NOTE]
>
>La valeur par défaut est `NO`et cette option charge uniquement les publicités à partir du point d’entrée actif actuel.

Par exemple :

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
