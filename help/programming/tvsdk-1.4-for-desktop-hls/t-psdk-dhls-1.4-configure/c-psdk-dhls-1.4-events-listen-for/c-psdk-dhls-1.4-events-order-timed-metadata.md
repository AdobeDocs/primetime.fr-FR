---
description: TVSDK distribue des événements de métadonnées minutés et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture change dans un manifeste. Les événements sont distribués dans l’ordre dans lequel ils apparaissent dans le manifeste.
title: Événements de métadonnées minutés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Événements de métadonnées minutés{#timed-metadata-events}

TVSDK distribue des événements de métadonnées minutés et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture change dans un manifeste. Les événements sont distribués dans l’ordre dans lequel ils apparaissent dans le manifeste.

Votre lecteur met en oeuvre des actions en fonction des événements suivants :

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: dispatché lorsqu’une métadonnée minutée ID3 était traitée.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: dispatché lorsque les métadonnées minutées étaient traitées et qu’aucune opportunité n’était détectée.
