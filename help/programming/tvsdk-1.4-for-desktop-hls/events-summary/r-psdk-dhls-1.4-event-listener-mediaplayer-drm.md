---
description: TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles.
seo-description: TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles.
seo-title: ÉVÉNEMENTS DRM
title: ÉVÉNEMENTS DRM
uuid: f1da5b31-3fad-4bb4-8aa3-3925d5f0e123
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# ÉVÉNEMENTS DRM{#drm-events}

TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles.

Pour être averti de tous les événements relatifs à la gestion des droits numériques, écoutez `DRMMetadataInfoEvent` pour les événements DRM contenant l&#39;objet `MediaPlayer`.

| Événement | Signification |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | De nouvelles métadonnées DRM sont disponibles. |