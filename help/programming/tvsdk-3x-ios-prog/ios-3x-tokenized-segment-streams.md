---
description: Les flux HLS distribués par l’intermédiaire d’un réseau de  de contenu (CDN) peuvent parfois utiliser des jetons d’authentification sur le manifeste et les demandes de segments pour vérification. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.
seo-description: Les flux HLS distribués par l’intermédiaire d’un réseau de  de contenu (CDN) peuvent parfois utiliser des jetons d’authentification sur le manifeste et les demandes de segments pour vérification. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie.
seo-title: Flux de segments jetés
title: Flux de segments jetés
uuid: 62e3b858-2605-4960-b504-9010674f80ad
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Flux de segments jetés {#tokenized-segment-streams}

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

