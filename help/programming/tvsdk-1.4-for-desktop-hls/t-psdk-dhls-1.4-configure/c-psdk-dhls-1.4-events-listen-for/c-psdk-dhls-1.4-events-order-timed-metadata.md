---
description: TVSDK distribue des événements de métadonnées minutés et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture change dans un manifeste. Les événements sont distribués dans l’ordre dans lequel ils apparaissent dans le manifeste.
seo-description: TVSDK distribue des événements de métadonnées minutés et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture change dans un manifeste. Les événements sont distribués dans l’ordre dans lequel ils apparaissent dans le manifeste.
seo-title: Événements de métadonnées minutés
title: Événements de métadonnées minutés
uuid: 69c43701-6ffa-45fe-a104-fe81391222e7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# Événements de métadonnées minutés{#timed-metadata-events}

TVSDK distribue des événements de métadonnées minutés et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture change dans un manifeste. Les événements sont distribués dans l’ordre dans lequel ils apparaissent dans le manifeste.

Votre lecteur implémente des actions en fonction des événements suivants :

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Distribué lorsqu’une métadonnée minutée ID3 a été traitée.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Distribué lorsque des métadonnées minutées ont été traitées et qu’aucune opportunité n’a été détectée.

