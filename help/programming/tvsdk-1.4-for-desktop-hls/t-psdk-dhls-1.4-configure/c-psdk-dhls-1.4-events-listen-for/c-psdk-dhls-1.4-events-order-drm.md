---
description: TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces événements.
seo-description: TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces événements.
seo-title: ÉVÉNEMENTS DRM
title: ÉVÉNEMENTS DRM
uuid: 729fe524-1047-4188-b4e6-96bfc5af4ae0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# ÉVÉNEMENTS DRM{#drm-events}

TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces événements.

Pour être informé de tous les événements relatifs à la gestion des droits numériques, veuillez tenir compte des points suivants :

```
DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE
```

L’exemple suivant illustre une progression type :

```
mediaPlayer.addEventListener(DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE,  
                             onDRMMetadataInfoAvailable);   
private function onDRMMetadataInfoAvailable(event:DRMMetadataInfoEvent){ 
    var drmMetadataInfo:DRMMetadataInfo = event.drmMetadataInfo; 
    ... 
} 
```

