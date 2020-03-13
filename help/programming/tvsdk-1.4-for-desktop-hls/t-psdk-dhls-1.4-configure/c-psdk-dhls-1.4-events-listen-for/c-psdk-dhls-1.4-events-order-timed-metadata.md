---
description: TVSDK distribue des  de métadonnées minutées et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture se modifie dans un manifeste. Les  sont distribuées dans l’ordre dans lequel elles apparaissent dans le manifeste.
seo-description: TVSDK distribue des  de métadonnées minutées et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture se modifie dans un manifeste. Les  sont distribuées dans l’ordre dans lequel elles apparaissent dans le manifeste.
seo-title: 'de métadonnées minutées '
title: 'de métadonnées minutées '
uuid: 69c43701-6ffa-45fe-a104-fe81391222e7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# de métadonnées minutées{#timed-metadata-events}

TVSDK distribue des  de métadonnées minutées et génère des métadonnées minutées chaque fois que des balises par défaut ou personnalisées sont rencontrées ou lorsqu’une liste de lecture se modifie dans un manifeste. Les  sont distribuées dans l’ordre dans lequel elles apparaissent dans le manifeste.

Votre lecteur implémente des actions en fonction du  suivant :

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Distribué lors du traitement d’une métadonnée chronométrée ID3.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Distribué lorsque des métadonnées minutées ont été traitées et qu’aucune opportunité n’a été détectée.

