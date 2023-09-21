---
description: TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques QoS, comme la mise en mémoire tampon ou la recherche.
title: Événements QoS
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Événements QoS{#qos-events}

TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques QoS, comme la mise en mémoire tampon ou la recherche.

Pour être averti de tous les événements liés à QoS, enregistrez une mise en oeuvre de `MediaPlayer.QOSEventListener` y compris les rappels suivants :

| Événement | Signification |
|---|---|
| [onBufferComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferComplete()) | La mise en mémoire tampon est terminée. |
| [onBufferStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferStart()) | La mise en mémoire tampon a commencé. |
| [onLoadInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onLoadInfo(com.adobe.mediacore.qos.LoadInfo))(loadInfo) | Un fragment a bien été téléchargé. |
| [onOperationFailed](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html)(MediaPlayerNotification. [Avertissement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) warning) | Une erreur récupérable s’est produite. |
| [onSeekComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekComplete(long))(long ajustTime) | La recherche est terminée. |
| [onSeekStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekStart()) | La recherche commence. |
