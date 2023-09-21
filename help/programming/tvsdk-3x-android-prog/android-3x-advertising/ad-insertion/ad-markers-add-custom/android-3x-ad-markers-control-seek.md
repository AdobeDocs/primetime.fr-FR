---
description: Vous pouvez remplacer le comportement par défaut de la façon dont TVSDK gère les recherches sur les publicités lors de l’utilisation de marqueurs d’annonce personnalisés.
title: Contrôle du comportement de lecture pour la recherche sur les marqueurs publicitaires personnalisés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Contrôle du comportement de lecture pour la recherche sur les marqueurs publicitaires personnalisés {#control-playback-behavior-for-seeking-over-custom-ad-markers}

Vous pouvez remplacer le comportement par défaut de la façon dont TVSDK gère les recherches sur les publicités lors de l’utilisation de marqueurs d’annonce personnalisés.

Par défaut, lorsqu’un utilisateur effectue une recherche dans ou dans des sections publicitaires antérieures résultant du placement de marqueurs publicitaires personnalisés, TVSDK ignore les publicités. Il peut s’agir d’une différence par rapport au comportement de lecture actuel pour les coupures publicitaires standard. Vous pouvez définir TVSDK pour repositionner le curseur de lecture au début de la dernière publicité personnalisée ignorée lorsque l’utilisateur effectue une recherche au-delà d’une ou de plusieurs publicités personnalisées.

1. Appeler `CustomRangeMetadata.setAdjustSeekPosition` avec `true`.

   ```java
   customRangeMetadata.setAdjustSeekPosition (true);
   ```

1. Utilisation `customRangeMetadata` in `MediaPlayerItemConfig`.

   ```java
   // Set customRangeMetadata 
   config.setCustomRangeMetadata(customRangeMetadata); 
   
   // prepare the content for playback by calling replaceCurrentResource 
   mediaPlayer.replaceCurrentResource(mediaResource, config); 
   ```
