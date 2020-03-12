---
description: TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles.
seo-description: TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles.
seo-title: DRM
title: DRM
uuid: c4d96e06-2268-4e38-9d05-68ccbe912484
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# DRM{#drm-events}

TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles.

Pour être informé de tous les  de DRM, enregistrez une implémentation de `MediaPlayer.DRMEventListener` qui inclut le rappel suivant.

| Event | Signification |
|---|---|
| [onDRMMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.DRMEventListener.html#onDRMMetadata(DRMMetadataInfo))`(DRMMetadataInfo drmMetadataInfo)` | De nouvelles métadonnées DRM sont disponibles. |

