---
description: TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces  de.
seo-description: TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces  de.
seo-title: DRM
title: DRM
uuid: 729fe524-1047-4188-b4e6-96bfc5af4ae0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# DRM{#drm-events}

TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces  de.

Pour être averti de tous les  de gestion des droits numériques, écoutez ce qui suit :

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

