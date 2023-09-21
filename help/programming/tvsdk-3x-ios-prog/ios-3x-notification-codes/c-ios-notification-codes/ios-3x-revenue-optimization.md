---
description: Ce tableau fournit des informations détaillées sur les notifications d’optimisation des recettes.
title: Code d’optimisation des recettes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# Code d’optimisation des recettes {#revenue-optimization-code}

Ce tableau fournit des informations détaillées sur les notifications d’OPTIMISATION DES RECETTES.

## Activation des rapports d’optimisation des recettes {#enable-revenue-optimization-reporting}

Pour activer ce rapport, utilisez l’api PTMediaPlayer : `[mediaPlayersetRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

>[!NOTE]
>
>La plupart des notifications d’informations contiennent des métadonnées pertinentes, par exemple l’URL de la ressource dont le téléchargement a échoué. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans le contenu audio alternatif ou dans une publicité.

| Code | Nom | Notification interne | Clés de métadonnées | Commentaires |
|---|---|---|---|---|
| 401001 | REVENUE_OPTIMIZATION_REPORTING | Aucun | Reportez-vous au tableau ci-dessous pour les clés de métadonnées basées sur différents événements. | Aucun |

| Détails de l’événement | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_START** Distribué dans TVSDK lorsque MediaPlayer::replaceCurrentResource est appelé. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, event, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolérance, zoneID, hasLivePreroll, adRequestTimeout, delayAdLoading, resourceType, creativeRepackagingTimeout abled, mediaId, clientId |
| **CONTENT_PLAYBACK_START** Distribué dans TVSDK lorsque le contenu est entré à l’état préparé et est prêt pour la lecture. Cet événement ne sera pas distribué à chaque chargement de manifeste ; il sera distribué uniquement au chargement initial. | clientTimestamp, contentURL, contentType, event, isLive, clientID |
| **AD_OPPORTUNITY_GENERATED** Distribué dans TVSDK lorsqu’une opportunité est générée. | clientTimestamp, event, opportunitésId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_START** Distribué dans TVSDK lorsqu’une opportunité commence à se résoudre. | clientTimestamp, event, opportunitésId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** Distribué dans TVSDK lorsqu’un résolveur d’annonces appelle MediaPlayerClient::notifyFailed(). Nécessité de renseigner les données | opportunitésId, notificationAD |
| **AD_RESOURCE_LOAD** Distribué lorsqu’une ressource publicitaire est récupérée par l’URL. responseStartTime : horodatage Unix pour le moment où la demande a commencé pour la première fois. responseTotalTime : durée totale (en secondes) nécessaire au chargement d’une réponse. responseStatus : code d’état rencontré lors de la récupération de la ressource. status:&quot;error&quot; ou &quot;success&quot; referrerAdId : identifiant de publicité référente qui a demandé la récupération de cette ressource (le cas échéant). referrerUrl : URL de référence qui a demandé la récupération de cette ressource. errorMessage : si le statut est &quot;erreur&quot;, la raison de l’erreur se trouve ici. | opportunitésId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referrerURL, referrerAdId |
| **AD_RESOURCE_LOAD_CRS** Distribué dans TVSDK lorsqu’un CRS est appliqué à une ressource, ainsi que la réponse pour le m3u8. resourceType : toujours &quot;crs&quot;. responseStartTime : horodatage Unix pour le moment où la demande a commencé pour la première fois. responseTotalTime : durée totale (en secondes) nécessaire au chargement d’une réponse. responseStatus : code d’état rencontré lors de la récupération de la ressource. status:&quot;error&quot; ou &quot;success&quot;. errorMessage : si le statut est &quot;erreur&quot;, la raison de l’erreur se trouve ici. mediaFileUrl : URL du fichier multimédia d’origine sélectionnée. mediaFileBitrate : débit du fichier multimédia sélectionné. mediaFileMimeType : type MIME du fichier multimédia sélectionné. url : URL de la ressource finale. | prospectId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_PLACE** Distribué dans TVSDK après qu’un adBreak a été placé sur la chronologie. Cet événement se produit une fois pour chaque coupure publicitaire. draftTime : heure à laquelle la coupure publicitaire a été demandée. realTime : heure à laquelle la coupure publicitaire a été réellement placée. PropositionsDuration : durée de la coupure publicitaire demandée pour insertion. Pour le contenu en direct, il s’agit de la durée de repère. Pour le contenu VOD, il s’agira normalement de -1. realDuration : durée réelle de la coupure publicitaire insérée. Calculé comme la durée totale de toutes les publicités, définie par leurs durées de segment respectives, ajoutées ou remplacées dans la chronologie du flux d’origine. purchasedAds : nombre de publicités dans la coupure publicitaire proposée. totalAds : nombre de publicités qui ont été placées avec succès. ads...n : les publicités correctement insérées seront insérées ici. Des informations complètes sur le manifeste de publicité peuvent être récupérées à partir de AD_OPPORTUNITY_RESOLVE_PROCESS | prospectId, statut, errorMessage, purchasedPropositionsDuration, realTime, realDuration, purchasedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_START** Distribué dans TVSDK après le début de la lecture d’une publicité. | clientTimestamp, event, id, url, duration, type, opportunitésId, clientId |
| **AD_PLAYBACK_COMPLETE** Distribué dans TVSDK après la lecture d’une publicité. | clientTimestamp, event, id, url, duration, type, opportunitésId, clientId |
| **ADBREAK_PLAYBACK_START** Distribué dans TVSDK lorsqu’un saut de publicité commence la lecture. | clientTimestamp, événement, opportunitésId, durée, heure, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** Distribué dans TVSDK lorsqu’un coupure publicitaire termine la lecture. | clientTimestamp, événement, opportunitésId, clientId |
| **CONTENT_PLAYBACK_COMPLETE** Distribué dans TVSDK une fois le contenu terminé. Cela peut se produire si le flux est remplacé, que le lecteur passe en état d’erreur, que le lecteur est réinitialisé ou que le contenu est réellement terminé. Cet événement sera nécessaire pour effectuer le suivi d’un sessionId. | clientTimestamp, event, clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** Distribué dans TVSDK lorsqu’une publicité a une erreur de lecture (erreurs de diffusion de variante). | événement, erreur, horodatage, manifestUrl, heure, opportunitéId, url |
