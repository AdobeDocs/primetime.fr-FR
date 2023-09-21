---
description: Les flux HLS diffusés par le biais d’un réseau de diffusion de contenu (CDN) peuvent parfois utiliser des jetons d’authentification sur les demandes de manifeste et de segment à vérifier. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.
title: Flux de segments jetés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Flux de segments jetés{#tokenized-segment-streams}

Les flux HLS diffusés par le biais d’un réseau de diffusion de contenu (CDN) peuvent parfois utiliser des jetons d’authentification sur les demandes de manifeste et de segment à vérifier. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.

Les jetons fournis en tant que cookies dans la réponse du manifeste principal (m3u8) ne sont pas partagés avec les requêtes de segment (ts), même si les requêtes de segment concernent le même domaine. Pour activer le partage de ces cookies dans une requête de segment, définissez la propriété suivante sur la variable `PTMetadata` instance fournie à l’élément de lecteur : 

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

Une requête supplémentaire est envoyée au manifeste maître (m3u8) avant que le flux ne commence à être lu.

>[!IMPORTANT]
>
>Cette fonctionnalité de partage de cookies n’est prise en charge que sur les appareils exécutant iOS 8 ou version ultérieure.
