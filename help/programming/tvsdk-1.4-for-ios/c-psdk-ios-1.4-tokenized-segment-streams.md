---
description: Les flux HLS diffusés par le biais d’un réseau CDN (Content Diffusion Network) peuvent parfois utiliser des jetons d’authentification sur les demandes de manifeste et de segmentation pour vérification. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.
title: Flux de segments jetés
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Flux de segments jetés{#tokenized-segment-streams}

Les flux HLS diffusés par le biais d’un réseau CDN (Content Diffusion Network) peuvent parfois utiliser des jetons d’authentification sur les demandes de manifeste et de segmentation pour vérification. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.

Les jetons fournis en tant que cookies dans la réponse du manifeste principal (m3u8) ne sont pas partagés avec les demandes de segment (ts) même si les demandes de segment concernent le même domaine. Pour activer le partage de ces cookies dans une demande de segment, définissez la propriété suivante sur l’instance `PTMetadata` fournie à l’élément du lecteur : 

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

Une requête supplémentaire est envoyée au manifeste maître (m3u8) avant que le flux ne commence à se lire.

>[!IMPORTANT]
>
>Cette fonctionnalité de partage de cookies n’est prise en charge que sur les appareils fonctionnant sous iOS 8 ou version ultérieure.

