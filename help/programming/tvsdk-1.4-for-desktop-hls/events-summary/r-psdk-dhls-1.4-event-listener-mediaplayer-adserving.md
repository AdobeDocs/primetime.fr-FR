---
description: TVSDK distribue des événements de diffusion publicitaire en réponse aux opérations de métadonnées minutées.
title: Événements de métadonnées de diffusion/minutage de publicité
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Événements de métadonnées de diffusion/minutage de publicité{#ad-serving-timed-metadata-events}

TVSDK distribue des événements de diffusion publicitaire en réponse aux opérations de métadonnées minutées.

Pour être averti de tous les événements associés, enregistrez les écouteurs d’événement avec la variable `MediaPlayer` pour les événements suivants.

| Événement | Signification |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | Les métadonnées minutées ID3 ont été traitées. |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | Une métadonnée minutée a été traitée et aucune opportunité n’a été détectée. |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | Les métadonnées minutées sont disponibles et aucune opportunité n’a été détectée. |
| TimedMetadataEvent.[TIMED_METADATA_IN_BACKGROUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | Les métadonnées minutées ont été traitées et aucune opportunité n’a été détectée dans le manifeste en arrière-plan. |
