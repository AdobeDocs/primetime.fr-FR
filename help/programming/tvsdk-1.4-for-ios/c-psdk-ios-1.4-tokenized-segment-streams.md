---
description: Les flux HLS distribués par l’intermédiaire d’un réseau de  de contenu (CDN) peuvent parfois utiliser des jetons d’authentification sur le manifeste et les demandes de segments pour vérification. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.
seo-description: Les flux HLS distribués par l’intermédiaire d’un réseau de  de contenu (CDN) peuvent parfois utiliser des jetons d’authentification sur le manifeste et les demandes de segments pour vérification. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.
seo-title: Flux de segments jetés
title: Flux de segments jetés
uuid: b17bb5bc-2029-4113-ac44-b1d30aa08ca6
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Flux de segments jetés{#tokenized-segment-streams}

Les flux HLS distribués par l’intermédiaire d’un réseau de  de contenu (CDN) peuvent parfois utiliser des jetons d’authentification sur le manifeste et les demandes de segments pour vérification. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.

Les jetons fournis en tant que cookies dans la réponse du manifeste principal (m3u8) ne sont pas partagés avec les demandes de segment (ts), même lorsque les demandes de segment sont pour le même domaine. Pour activer le partage de ces cookies dans une requête de segment, définissez la propriété suivante sur l’ `PTMetadata` instance fournie à l’élément du lecteur :

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

Une requête supplémentaire est envoyée au manifeste maître (m3u8) avant que le flux ne commence à se lire.

>[!IMPORTANT]
>
>Cette fonctionnalité de partage de cookies est uniquement prise en charge sur les périphériques exécutant iOS 8 ou une version ultérieure.

