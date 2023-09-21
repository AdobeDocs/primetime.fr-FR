---
description: TVSDK distribue des événements DRM (Digital Rights Management, gestion des droits numériques) en réponse aux opérations liées à DRM, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut mettre en oeuvre des actions en réponse à ces événements.
title: Événements DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Événements DRM{#drm-events}

TVSDK distribue des événements DRM (Digital Rights Management, gestion des droits numériques) en réponse aux opérations liées à DRM, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut mettre en oeuvre des actions en réponse à ces événements.

Pour être averti de tous les événements liés à DRM, écoutez ce qui suit :

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
