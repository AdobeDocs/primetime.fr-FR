---
description: TVSDK distribue des événements de métadonnées minutés et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture change dans un manifeste. Les événements sont distribués dans l’ordre dans lequel ils apparaissent dans le manifeste.
title: Événements de métadonnées minutés
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# Événements de métadonnées minutés{#timed-metadata-events}

TVSDK distribue des événements de métadonnées minutés et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture change dans un manifeste. Les événements sont distribués dans l’ordre dans lequel ils apparaissent dans le manifeste.

Votre lecteur implémente des actions en fonction des événements suivants :

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Distribué lorsqu’une métadonnée minutée ID3 a été traitée.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Distribué lorsque des métadonnées minutées ont été traitées et qu’aucune opportunité n’a été détectée.

