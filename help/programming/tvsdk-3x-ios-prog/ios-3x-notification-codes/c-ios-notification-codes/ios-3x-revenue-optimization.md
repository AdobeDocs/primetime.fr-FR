---
description: 'Ce tableau fournit des informations détaillées sur les notifications d''optimisation des recettes. '
seo-description: 'Ce tableau fournit des informations détaillées sur les notifications d''optimisation des recettes. '
seo-title: Code d'optimisation des recettes
title: Code d'optimisation des recettes
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Code d&#39;optimisation des recettes {#revenue-optimization-code}

Ce tableau fournit des informations détaillées sur les notifications d’OPTIMISATION DES RECETTES.

## Activer le d&#39;optimisation des recettes {#enable-revenue-optimization-reporting}

Pour activer cette , utilisez l’API PTMediaPlayer : `[mediaPlayer
setRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

[!NRemarque]: La plupart des notifications d’informations contiennent des métadonnées appropriées, par exemple l’URL de la ressource qui n’a pas été téléchargée. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans le contenu audio alternatif ou dans une publicité.

|Code|Name|Notification interne|Clés de métadonnées|Commentaires||—|—|—|—|—|—||401001| REVENUE_OPTIMIZATION_| Aucun| Reportez-vous au tableau ci-dessous pour les clés de métadonnées en fonction de différents  de. | Aucun|

| Détails  | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_** distribué dans TVSDK lorsque MediaPlayer::replaceCurrentResource est appelé. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll,, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolérance, zoneID, hasLivePreroll, adRequestTimeout, delayAdLoading, resourceType, creativeRepackaging Activé, mediaId, clientId |
| **CONTENT_PLAYBACK_** distribué dans TVSDK lorsque le contenu est entré dans l’état préparé et est prêt pour la lecture. Ce ne sera pas distribué lors de chaque transfert de manifeste ; il ne sera distribué que lors du chargement initial. | clientTimestamp, contentURL, contentType,, isLive, clientID |
| **AD_OPPORTUNITY_GENERATED** Distribué dans TVSDK lorsqu’une opportunité est générée. | clientTimestamp,, OpportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_** distribué dans TVSDK lorsqu’une opportunité commence à se résoudre. | clientTimestamp,, OpportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** Distribué dans TVSDK lorsqu’un résolveur d’annonce appelle MediaPlayerClient::notificationFailed(). Besoin de renseigner les données | opportunitiesId, notificationAD |
| **AD_RESOURCE_LOAD** Distribué lorsqu’une ressource publicitaire est récupérée par l’URL. responseStartTime : horodatage Unix pour le premier démarrage de la requête. responseTotalTime : durée totale (en secondes) nécessaire au chargement d’une réponse. responseStatus : code d’état rencontré lors de la récupération de la ressource. status:&quot;error&quot; ou &quot;success&quot; referrerAdId : identifiant de publicité référente qui a demandé la récupération de cette ressource (le cas échéant). referrerUrl : URL de référence qui a demandé la récupération de cette ressource. errorMessage : si l’état est &quot;error&quot;, la raison de l’erreur se trouve ici. | opportunitiesId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referrerURL, referrerAdId |
| **AD_RESOURCE_LOAD_CRS** Distribué dans TVSDK lorsqu’un CRS est appliqué à un fichier, ainsi que la réponse du m3u8. resourceType:always &quot;crs&quot;. responseStartTime : horodatage Unix pour le premier démarrage de la requête. responseTotalTime : durée totale (en secondes) nécessaire au chargement d’une réponse. responseStatus : code d’état rencontré lors de la récupération de la ressource. status: &quot;error&quot; ou &quot;success&quot;. errorMessage : si l’état est &quot;error&quot;, la raison de l’erreur se trouve ici. mediaFileUrl : URL du fichier multimédia d’origine sélectionnée. mediaFileBitrate : débit du fichier multimédia sélectionné. mediaFileMimeType : Type MIME du fichier multimédia sélectionné. url : URL de ressource finale. | opportunitiesId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_PLACE** Distribué dans TVSDK après qu’une publicitéBreak a été placée sur la chronologie. Ce  se produira une fois pour chaque coupure publicitaire. proposéTime : heure à laquelle la coupure publicitaire a été demandée. currentTime : heure à laquelle la coupure publicitaire a été réellement placée. proposéDuration : durée de la coupure publicitaire qui a été demandée pour insertion. Pour le contenu en direct, il s’agit de la durée du signal. Pour le contenu VOD, il s’agirait normalement de -1. currentDuration : durée réelle de la coupure publicitaire insérée. Calculé comme la durée totale de toutes les publicités, définie par leur durée de segment respective, ajoutée ou remplacée dans le plan de montage chronologique du flux d’origine. propsPublicités : nombre de publicités dans la coupure publicitaire proposée. totalPublicités : nombre de publicités qui ont bien été placées. publicités...n:Les publicités insérées avec succès seront insérées ici. Des informations complètes du manifeste publicitaire peuvent être récupérées à partir d&#39;AD_OPPORTUNITY_RESOLVE_PROCESS | opportunitiesId, status, errorMessage, proposéTime, proposéDuration, realTime, realDuration, proposéAds, totalAds, ads_id, ads_type, ads_term, ads_url |
| **AD_PLAYBACK_** distribué dans TVSDK après le début de la lecture d’une publicité. | clientTimestamp,, id, url, length, type, OpportunityId, clientId |
| **AD_PLAYBACK_COMPLETE** Distribué dans TVSDK après la fin de la lecture d’une publicité. | clientTimestamp,, id, url, length, type, OpportunityId, clientId |
| **ADBREAK_PLAYBACK_** Distribué dans TVSDK lorsqu’un adbreak  la lecture. | clientTimestamp,, OpportunityId, durée, time, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** Distribué dans TVSDK lorsqu’un adbreak termine la lecture. | clientTimestamp,, opportunitiesId, clientId |
| **CONTENT_PLAYBACK_COMPLETE** Distribué dans TVSDK lorsque tout contenu est terminé.Cela peut se produire si le flux est remplacé, si le lecteur entre dans un état d’erreur, si le lecteur est réinitialisé ou si le contenu est réellement terminé. Ce  sera nécessaire pour effectuer le suivi d’un ID de session. | clientTimestamp, , clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** Distribué dans TVSDK lorsqu’une publicité comporte une erreur de lecture (erreurs de flux de variantes). | , erreur, horodatage, manifestUrl, time, OpportunityId, url |