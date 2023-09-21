---
description: TVSDK distribue des événements DRM (Digital Rights Management, gestion des droits numériques) en réponse aux opérations liées à DRM, comme lorsque de nouvelles métadonnées DRM deviennent disponibles.
title: Événements DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# Événements DRM{#drm-events}

TVSDK distribue des événements DRM (Digital Rights Management, gestion des droits numériques) en réponse aux opérations liées à DRM, comme lorsque de nouvelles métadonnées DRM deviennent disponibles.

Pour être averti de tous les événements liés à DRM, écoutez `DRMMetadataInfoEvent` pour les événements DRM avec `MediaPlayer` .

| Événement | Signification |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | De nouvelles métadonnées DRM sont disponibles. |
