---
description: 'Ce tableau fournit des informations détaillées sur les notifications d''optimisation des recettes. '
seo-description: 'Ce tableau fournit des informations détaillées sur les notifications d''optimisation des recettes. '
seo-title: Code d'optimisation des recettes
title: Code d'optimisation des recettes
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Code d&#39;optimisation des recettes {#revenue-optimization-code}

Ce tableau fournit des informations détaillées sur les notifications d&#39;OPTIMISATION DES RECETTES.

## Activer le Rapports d&#39;optimisation des recettes {#enable-revenue-optimization-reporting}

Pour activer ce rapports, utilisez l’api PTMediaPlayer : `[mediaPlayer
setRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

[!Nnote]: La plupart des notifications d’informations contiennent des métadonnées pertinentes, par exemple l’URL de la ressource qui n’a pas été téléchargée. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans l’autre contenu audio ou dans une publicité.

|Code |Nom |Notification interne |Clés de métadonnées |Commentaires |
|—|—|—|—|—|||
|401001 | REVENUE_OPTIMIZATION_RAPPORTS | Aucun | Reportez-vous au tableau ci-dessous pour les clés de métadonnées basées sur différents événements. | Aucun |

| Détails du Événement | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_DÉBUT** Distribué dans TVSDK lorsque MediaPlayer::replaceCurrentResource est appelé. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, événement, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adRequestTimeout, delayAdLoading, resourceType, creativeRepackaging Activé, mediaId, clientId |
| **CONTENT_PLAYBACK_DÉBUT** Distribué dans TVSDK lorsque le contenu est entré dans l’état préparé et est prêt pour la lecture. Ce événement n&#39;est pas distribué pour chaque transfert de manifeste ; il ne l&#39;est que pour le chargement initial. | clientTimestamp, contentURL, contentType, événement, isLive, clientID |
| **AD_OPPORTUNITY_GENERATED** Distribué dans TVSDK lorsqu’une opportunité est générée. | clientTimestamp, événement, opportunitiesId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_DÉBUT** Distribué dans TVSDK lorsqu’une opportunité commence à être résolue. | clientTimestamp, événement, opportunitiesId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** Distribué dans TVSDK lorsqu’un résolveur d’annonces appelle MediaPlayerClient::notificationFailed(). Besoin de renseigner des données | opportunitiesId, notificationAD |
| **AD_RESOURCE_LOAD** Distribué lorsqu’une ressource publicitaire est récupérée par l’URL. responseStartTime : horodatage Unix pour le premier démarrage de la demande. responseTotalTime : durée totale (en secondes) nécessaire au chargement d’une réponse. responseStatus : code d&#39;état rencontré lors de la récupération de la ressource. status:&quot;error&quot; ou &quot;success&quot; referrerAdId : identifiant de publicité référente qui a demandé la récupération de cette ressource (le cas échéant). referrerUrl : URL de référence qui a demandé la récupération de cette ressource. errorMessage : si l’état est &quot;error&quot;, la raison de l’erreur se trouve ici. | opportunitiesId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referrerURL, referrerAdId |
| **AD_RESOURCE_LOAD_CRS** Distribué dans TVSDK lorsqu’un CRS est appliqué à un fichier, ainsi que la réponse du m3u8. resourceType:always &quot;crs&quot;. responseStartTime : horodatage Unix pour le premier démarrage de la demande. responseTotalTime : durée totale (en secondes) nécessaire au chargement d’une réponse. responseStatus : code d&#39;état rencontré lors de la récupération de la ressource. status:&quot;error&quot; ou &quot;success&quot;. errorMessage : si l’état est &quot;error&quot;, la raison de l’erreur se trouve ici. mediaFileUrl : URL du fichier multimédia d’origine sélectionnée. mediaFileBitrate : débit du fichier multimédia sélectionné. mediaFileMimeType : Type MIME du fichier multimédia sélectionné. url : URL de ressource finale. | opportunitiesId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_PLACE** Distribué dans TVSDK après qu’un adBreak a été placé sur la chronologie. Ce événement se produit une fois pour chaque coupure publicitaire. proposéTime : heure à laquelle la coupure publicitaire a été demandée. realTime : heure à laquelle la coupure publicitaire a été réellement placée. proposéDuration : durée de la coupure publicitaire demandée pour insertion. Pour le contenu en direct, il s’agirait de la durée du signal. Pour le contenu VOD, il s’agirait normalement de -1. realDuration : durée réelle de la coupure publicitaire insérée. Calculé comme la durée totale de toutes les publicités, définie par leurs durées de segment respectives, ajoutée ou remplacée dans le plan de montage chronologique du flux d’origine. Annonces proposées : nombre de publicités dans la coupure publicitaire proposée. totalPublicités : nombre de publicités qui ont été placées avec succès. publicités...n : Les publicités insérées avec succès seront insérées ici. Des informations complètes du manifeste publicitaire peuvent être récupérées dans AD_OPPORTUNITY_RESOLVE_PROCESS. | opportunitiesId, status, errorMessage, proposéTime, proposéDuration, realTime, trueDuration, proposéPublicités, totalPublicités, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_DÉBUT** distribué dans TVSDK après le début de la lecture d’une publicité. | clientTimestamp, événement, id, url, duration, type, opportunitiesId, clientId |
| **AD_PLAYBACK_COMPLETE** Distribué dans TVSDK après la lecture d’une publicité. | clientTimestamp, événement, id, url, duration, type, opportunitiesId, clientId |
| **ADBREAK_PLAYBACK_DÉBUT** Distribué dans TVSDK lorsqu’un adbreak début la lecture. | clientTimestamp, événement, OpportunityId, duration, time, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** Distribué dans TVSDK lorsqu’un adbreak termine la lecture. | clientTimestamp, événement, opportunitiesId, clientId |
| **CONTENT_PLAYBACK_COMPLETE** Distribué dans TVSDK une fois le contenu terminé.Cela peut se produire si le flux est remplacé, si le lecteur entre en état d’erreur, si le lecteur est réinitialisé ou si le contenu est réellement terminé. Ce événement sera nécessaire pour effectuer le suivi d&#39;un ID de session. | clientTimestamp, événement, clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** Distribué dans TVSDK lorsqu’une publicité comporte une erreur de lecture (erreurs de flux de variantes). | événement, erreur, horodatage, manifestUrl, time, opportunitiesId, url |