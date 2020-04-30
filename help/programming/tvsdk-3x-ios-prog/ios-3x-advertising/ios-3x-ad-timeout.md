---
description: Vous pouvez insérer des publicités dans votre contenu VOD et du contenu direct/linéaire à l’aide de l’interface de prise de décision publicitaire d’Adobe Primetime.
seo-description: Vous pouvez insérer des publicités dans votre contenu VOD et du contenu direct/linéaire à l’aide de l’interface de prise de décision publicitaire d’Adobe Primetime.
seo-title: Exigences en matière de publicité
title: Exigences en matière de publicité
uuid: 0287f1e4-746f-42e5-b811-409064dd9b13
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Expiration de la publicité {#ad-timeout}

## Exigences de la fondation AV {#av-foundation-requirements}

Dans le cas d’un contenu VOD, l’assemblage de la liste de lecture, qui implique le chargement du manifeste de contenu principal, la résolution de la publicité et le chargement du manifeste de la publicité, doit être terminé dans les 35 secondes.

En cas de contenu en direct, chaque fois que la liste de lecture est mise à jour, l’assemblage de la liste de lecture doit être terminé dans les 20 secondes.

**API pertinentes pour le délai d’expiration AdResolution**

```
/** @name Properties */
/** The default timeout value (in seconds) for resolution of ad requests is 15 seconds.
*
*/
*
@property (notatomic, assign) double adResolutionTimeout;
```

Vous pouvez définir adResolutionTimeout en définissant PTAdMetadata::adResolutionTimeout lors de la configuration des métadonnées de votre publicité.

```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adResolutionTimeout = 15 seconds
```

Suivez ensuite la section : [Métadonnées](../..//tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md)du serveur et de Primetime.

**API relatives au délai d’expiration d’AdManifest**

```
/** @name Properties */
 /** The default timeout value (in seconds) for loading of ad manifests is 5 seconds.
 *
 */
 *
 @property (notatomic, assign) double adManifestTimeout; 
```

Vous pouvez définir adManifestTimeout en définissant PTAdMetadata::adManifestTimeout lors de la configuration des métadonnées de votre publicité.


```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adManifestTimeout = 5 seconds
```

Suivez ensuite la section : [Métadonnées](../..//tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md)du serveur et de Primetime.
