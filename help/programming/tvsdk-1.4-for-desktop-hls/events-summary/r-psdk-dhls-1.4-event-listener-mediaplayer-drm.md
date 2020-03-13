---
description: TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles.
seo-description: TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles.
seo-title: DRM
title: DRM
uuid: f1da5b31-3fad-4bb4-8aa3-3925d5f0e123
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# DRM{#drm-events}

TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles.

Pour être averti de tous les  de DRM, écoutez `DRMMetadataInfoEvent` les DRM avec l’ `MediaPlayer` objet.

| Event | Signification |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | De nouvelles métadonnées DRM sont disponibles. |