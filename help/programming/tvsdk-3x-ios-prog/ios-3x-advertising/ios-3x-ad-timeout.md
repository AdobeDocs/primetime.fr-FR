---
description: Vous pouvez insérer des publicités dans votre contenu VOD et linéaire à l’aide de l’interface de prise de décision publicitaire d’Adobe Primetime.
title: Exigences publicitaires
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Expiration de la publicité {#ad-timeout}

## Exigences A/V {#av-foundation-requirements}

Dans le cas du contenu VOD, le groupement de liste de lecture, qui implique le chargement principal du manifeste de contenu, de la résolution de publicité et du chargement du manifeste de publicité, doit être terminé dans les 35 secondes.

En cas de contenu en direct, chaque fois que la liste de lecture est mise à jour, le regroupement des listes de lecture doit être effectué dans les 20 secondes.

**API relatives au délai d’expiration AdResolution**

```
/** @name Properties */
/** The default timeout value (in seconds) for resolution of ad requests is 15 seconds.
*
*/
*
@property (notatomic, assign) double adResolutionTimeout;
```

Vous pouvez définir adResolutionTimeout en définissant PTAdMetadata::adResolutionTimeout lors de la configuration de vos métadonnées publicitaires.

```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adResolutionTimeout = 15 seconds
```

Suivez ensuite la section : [Métadonnées du serveur de publicités Primetime](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).

**API relatives au délai d’expiration d’AdManifest**

```
/** @name Properties */
 /** The default timeout value (in seconds) for loading of ad manifests is 5 seconds.
 *
 */
 *
 @property (notatomic, assign) double adManifestTimeout; 
```

Vous pouvez définir adManifestTimeout en définissant PTAdMetadata::adManifestTimeout lors de la configuration de vos métadonnées publicitaires.


```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adManifestTimeout = 5 seconds
```

Suivez ensuite la section : [Métadonnées du serveur de publicités Primetime](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).
