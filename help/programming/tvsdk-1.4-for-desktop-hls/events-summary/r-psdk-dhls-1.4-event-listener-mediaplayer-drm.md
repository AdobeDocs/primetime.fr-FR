---
description: TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles.
title: ÉVÉNEMENTS DRM
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---


# ÉVÉNEMENTS DRM{#drm-events}

TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles.

Pour être averti de tous les événements relatifs à la gestion des droits numériques, écoutez `DRMMetadataInfoEvent` pour les événements DRM contenant l&#39;objet `MediaPlayer`.

| Événement | Signification |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | De nouvelles métadonnées DRM sont disponibles. |