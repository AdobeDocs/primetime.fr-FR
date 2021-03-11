---
description: TVSDK distribue des événements de service publicitaire en réponse à des opérations de métadonnées minutées.
title: Événements de métadonnées de diffusion/minutage de publicité
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Événements de métadonnées de diffusion/minutage de publicité{#ad-serving-timed-metadata-events}

TVSDK distribue des événements de service publicitaire en réponse à des opérations de métadonnées minutées.

Pour être averti de tous ces événements connexes, enregistrez les auditeurs de événement avec l&#39;objet `MediaPlayer` pour les événements suivants.

| Événement | Signification |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_AJOUTÉ](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | Les métadonnées minutées ID3 ont été traitées. |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | Une métadonnée minutée a été traitée et aucune opportunité n&#39;a été détectée. |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | Les métadonnées minutées sont disponibles et aucune opportunité n’a été détectée. |
| TimedMetadataEvent.[TIMED_METADATA_IN_BACKGROUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | Les métadonnées minutées ont été traitées et aucune opportunité n&#39;a été détectée dans le manifeste d&#39;arrière-plan. |