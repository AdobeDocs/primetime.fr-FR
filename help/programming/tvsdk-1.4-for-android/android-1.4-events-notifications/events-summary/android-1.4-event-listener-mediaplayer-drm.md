---
description: TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles.
seo-description: TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles.
seo-title: ÉVÉNEMENTS DRM
title: ÉVÉNEMENTS DRM
uuid: c4d96e06-2268-4e38-9d05-68ccbe912484
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# ÉVÉNEMENTS DRM{#drm-events}

TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles.

Pour être informé de tous les événements relatifs à la gestion des droits numériques, enregistrez une implémentation de `MediaPlayer.DRMEventListener` qui inclut le rappel suivant.

| Événement | Signification |
|---|---|
| [onDRMMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.DRMEventListener.html#onDRMMetadata(DRMMetadataInfo)) `(DRMMetadataInfo drmMetadataInfo)` | De nouvelles métadonnées DRM sont disponibles. |

