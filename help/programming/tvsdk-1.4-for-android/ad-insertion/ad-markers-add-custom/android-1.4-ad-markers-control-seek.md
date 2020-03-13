---
description: Vous pouvez remplacer le comportement par défaut de la recherche de TVSDK sur les publicités lors de l’utilisation de marqueurs publicitaires personnalisés.
seo-description: Vous pouvez remplacer le comportement par défaut de la recherche de TVSDK sur les publicités lors de l’utilisation de marqueurs publicitaires personnalisés.
seo-title: Contrôler le comportement de lecture pour la recherche par rapport aux marqueurs publicitaires personnalisés
title: Contrôler le comportement de lecture pour la recherche par rapport aux marqueurs publicitaires personnalisés
uuid: cf973caf-be29-46ce-bfa4-651e7653f8d4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Contrôler le comportement de lecture pour la recherche par rapport aux marqueurs publicitaires personnalisés{#control-playback-behavior-for-seeking-over-custom-ad-markers}

Vous pouvez remplacer le comportement par défaut de la recherche de TVSDK sur les publicités lors de l’utilisation de marqueurs publicitaires personnalisés.

Par défaut, lorsqu’un utilisateur effectue une recherche dans des sections publicitaires ou au-delà résultant de l’emplacement de marques publicitaires personnalisées, TVSDK ignore les publicités. Cela peut différer du comportement de lecture actuel pour les coupures publicitaires standard.

Vous pouvez demander à TVSDK de repositionner le curseur de lecture au début de la dernière publicité personnalisée ignorée lorsque l’utilisateur effectue une recherche au-delà d’une ou plusieurs publicités personnalisées.

1. Configurez une instance de métadonnées avec le  de `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` défini sur la valeur de chaîne &quot;true&quot; (et non sur une valeur booléenne `true`).

   ```java
   Metadata metadata = new MetadataNode(); 
   metadata.setValue(DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED.getValue(),"true");
   ```

1. Créez et configurez une `MediaResource` instance en transmettant les options de configuration supplémentaires à `TimeRangeCollection.toMetadata`. Cette méthode reçoit des options de configuration supplémentaires via une autre structure de métadonnées générique.

   ```java
   MediaResource mediaResource =  
     MediaResource.createFromUrl("www.example.com/video/test_video.m3u8", 
                                 timeRanges.toMetadata(metadata));
   ```

