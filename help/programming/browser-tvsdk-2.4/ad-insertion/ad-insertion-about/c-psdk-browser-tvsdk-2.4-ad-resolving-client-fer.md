---
description: Le contenu de relecture d’événement complet (FER) est un flux en direct converti en VOD en ajoutant la balise
title: Résoudre et insertion des publicités FER
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Résoudre et insertion des publicités FER{#fer-ad-resolving-and-insertion}

Le contenu de relecture d’événement complet (FER) est un flux en direct converti en VOD en ajoutant la balise #EXT-X-ENDLIST à la fin du fichier de manifeste. Le flux conserve ses marqueurs de repère de publicité.

Le navigateur TVSDK traite un flux FER comme VOD. Par défaut, le mode de signalisation de la publicité est `SERVER_MAP`. Cependant, comme le flux conserve ses marqueurs de repère de publicité, vous pouvez définir le mode de signal publicitaire sur `MANIFEST_CUES`, qui vous permet d’utiliser les marqueurs de repère de publicité pour l’insertion de publicités.

Pour activer l’insertion de publicités à l’aide de marqueurs de repère pour un flux FER :

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

Le comportement de résolution et d’insertion des publicités FER est similaire à celui de la résolution et de l’insertion des publicités en direct. Le navigateur TVSDK effectue les opérations suivantes :

1. Insère des publicités preroll au début du contenu.
1. Résout les publicités spécifiées par les points de repère définis dans le manifeste.
1. Remplace des parties du contenu principal par des coupures publicitaires de la même durée.
1. recalcule la chronologie virtuelle, si nécessaire.

**Restriction :** Le navigateur TVSDK ne prend en charge que la lecture des flux de flux HLS FER. En outre, les publicités mid-roll MP4 ne sont pas prises en charge avec les flux FER.
