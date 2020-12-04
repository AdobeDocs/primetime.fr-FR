---
description: 'Le contenu Replay Événement complet (FER) est un flux en direct converti en VOD en ajoutant la balise #EXT-X-ENDLIST à la fin du fichier manifeste. Le flux conserve ses marqueurs publicitaires.'
seo-description: 'Le contenu Replay Événement complet (FER) est un flux en direct converti en VOD en ajoutant la balise #EXT-X-ENDLIST à la fin du fichier manifeste. Le flux conserve ses marqueurs publicitaires.'
seo-title: Résolution et insertion des annonces FER
title: Résolution et insertion des annonces FER
uuid: 85da0e92-17fe-4001-a53c-085dadd09756
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Résolution et insertion de publicités FER{#fer-ad-resolving-and-insertion}

Le contenu Replay Événement complet (FER) est un flux en direct converti en VOD en ajoutant la balise #EXT-X-ENDLIST à la fin du fichier manifeste. Le flux conserve ses marqueurs publicitaires.

Le navigateur TVSDK traite un flux FER comme VOD, de sorte que par défaut, le mode de signalisation de la publicité est `SERVER_MAP`. Cependant, comme le flux conserve ses marqueurs de indices publicitaires, vous pouvez définir le mode de signalisation de la publicité sur `MANIFEST_CUES`, ce qui vous permet d’utiliser les marqueurs de indices publicitaires pour l’insertion de publicités.

Pour activer l’insertion publicitaire à l’aide de marqueurs de repère pour un flux FER :

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

Le comportement de résolution et d’insertion des annonces FER est similaire à celui de la résolution et de l’insertion des annonces en direct. Le navigateur TVSDK effectue les opérations suivantes :

1. Insère toute publicité preroll au début du contenu.
1. Résout les publicités spécifiées par les indices définis dans le manifeste.
1. Remplace certaines parties du contenu principal par des coupures publicitaires de même durée.
1. recalcule la chronologie virtuelle, si nécessaire.

**Restriction : le** navigateur TVSDK ne prend en charge que la lecture en flux continu HLS FER. En outre, les publicités MP4 milieu de gamme ne sont pas prises en charge avec les flux FER.
