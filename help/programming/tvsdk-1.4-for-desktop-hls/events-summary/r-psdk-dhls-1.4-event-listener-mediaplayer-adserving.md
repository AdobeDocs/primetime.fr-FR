---
description: TVSDK distribue des  de service publicitaire en réponse aux opérations de métadonnées minutées.
seo-description: TVSDK distribue des  de service publicitaire en réponse aux opérations de métadonnées minutées.
seo-title: 'de métadonnées de diffusion/minutage de publicité '
title: 'de métadonnées de diffusion/minutage de publicité '
uuid: fd50a937-0c9b-4c47-acb2-1ffc0592ad54
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# de métadonnées de diffusion/minutage de publicité{#ad-serving-timed-metadata-events}

TVSDK distribue des  de service publicitaire en réponse aux opérations de métadonnées minutées.

Pour être averti de tous ces  de connexes, inscrivez les auditeurs de avec l&#39; `MediaPlayer` objet pour l&#39; suivante.

| Event | Signification |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | Les métadonnées minutées ID3 ont été traitées. |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | Une métadonnée minutée a été traitée et aucune opportunité n’a été détectée. |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | Les métadonnées minutées sont disponibles et aucune opportunité n’a été détectée. |
| TimedMetadataEvent.[TIMED_METADATA_IN_BACKGROUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | Les métadonnées minutées ont été traitées et aucune opportunité n’a été détectée dans le manifeste d’arrière-plan. |