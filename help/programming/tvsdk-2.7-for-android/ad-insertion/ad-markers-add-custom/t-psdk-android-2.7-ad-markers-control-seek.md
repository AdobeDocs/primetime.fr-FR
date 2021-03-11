---
description: Vous pouvez remplacer le comportement par défaut de la façon dont TVSDK traite les recherches sur les publicités lors de l’utilisation de marqueurs publicitaires personnalisés.
title: Contrôler le comportement de lecture pour la recherche sur les marques publicitaires personnalisées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Contrôler le comportement de lecture pour la recherche sur les marques publicitaires personnalisées {#control-playback-behavior-for-seeking-over-custom-ad-markers}

Vous pouvez remplacer le comportement par défaut de la façon dont TVSDK traite les recherches sur les publicités lors de l’utilisation de marqueurs publicitaires personnalisés.

Par défaut, lorsqu’un utilisateur effectue des recherches dans ou après des sections d’annonces résultant de l’emplacement de marques publicitaires personnalisées, TVSDK ignore les publicités. Ceci peut différer du comportement de lecture actuel pour les pauses publicitaires standard. Vous pouvez définir TVSDK pour repositionner le curseur de lecture au début de la dernière publicité personnalisée ignorée lorsque l’utilisateur recherche au-delà d’une ou plusieurs publicités personnalisées.

1. Appelez `CustomRangeMetadata.setAdjustSeekPosition` avec `true`.

   ```java
   customRangeMetadata.setAdjustSeekPosition (true);
   ```

1. Utilisez `customRangeMetadata` dans `MediaPlayerItemConfig`.

   ```java
   // Set customRangeMetadata 
   config.setCustomRangeMetadata(customRangeMetadata); 
   
   // prepare the content for playback by calling replaceCurrentResource 
   mediaPlayer.replaceCurrentResource(mediaResource, config); 
   ```

