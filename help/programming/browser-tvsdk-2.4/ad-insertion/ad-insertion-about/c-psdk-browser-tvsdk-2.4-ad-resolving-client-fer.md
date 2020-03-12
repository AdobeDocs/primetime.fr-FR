---
description: 'Le contenu  replay complet (FER) est un flux en direct converti en VOD en ajoutant la balise #EXT-X-ENDLIST à la fin du fichier manifeste. Le flux conserve ses marqueurs de signaux publicitaires.'
seo-description: 'Le contenu  replay complet (FER) est un flux en direct converti en VOD en ajoutant la balise #EXT-X-ENDLIST à la fin du fichier manifeste. Le flux conserve ses marqueurs de signaux publicitaires.'
seo-title: Résolution et insertion des publicités FER
title: Résolution et insertion des publicités FER
uuid: 85da0e92-17fe-4001-a53c-085dadd09756
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Résolution et insertion des publicités FER{#fer-ad-resolving-and-insertion}

Le contenu  replay complet (FER) est un flux en direct converti en VOD en ajoutant la balise #EXT-X-ENDLIST à la fin du fichier manifeste. Le flux conserve ses marqueurs de signaux publicitaires.

Le navigateur TVSDK traite un flux FER comme VOD, de sorte que le mode de signalisation de la publicité est par défaut `SERVER_MAP`. Cependant, puisque le flux conserve ses marqueurs de repère d’annonce, vous pouvez définir le mode de signalisation de l’annonce sur `MANIFEST_CUES`, ce qui vous permet d’utiliser les marqueurs de repère d’annonce pour l’insertion de l’annonce.

Pour activer l’insertion publicitaire à l’aide de marqueurs de repère pour un flux FER :

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

Le comportement de résolution et d’insertion des publicités FER est similaire à celui de la résolution et de l’insertion des publicités en direct. Le navigateur TVSDK effectue les opérations suivantes :

1. Insère les publicités preroll au début du contenu.
1. Résout les publicités spécifiées par les indices définis dans le manifeste.
1. Remplace certaines parties du contenu principal par des coupures publicitaires de même durée.
1. Recalcule la chronologie virtuelle, si nécessaire.

**Restriction :** Le navigateur TVSDK ne prend en charge que la lecture des flux FER HLS. En outre, les publicités MP4 milieu de gamme ne sont pas prises en charge avec les flux FER.
