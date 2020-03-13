---
description: TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de qualité de service (mise en mémoire tampon ou recherche, par exemple).
seo-description: TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de qualité de service (mise en mémoire tampon ou recherche, par exemple).
seo-title: ' QoS'
title: ' QoS'
uuid: 27f60cd3-d3fc-4ea3-81df-96d0fe9f7068
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


#  QoS{#qos-events}

TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de qualité de service (mise en mémoire tampon ou recherche, par exemple).

Pour être averti de tous les  de la qualité de service, enregistrez une mise en oeuvre de `MediaPlayer.QOSEventListener` incluant les rappels suivants :

| Event | Signification |
|---|---|
| [onBufferComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferComplete()) | La mise en mémoire tampon est terminée. |
| [onBufferStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferStart()) | La mise en mémoire tampon a commencé. |
| [onLoadInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onLoadInfo(com.adobe.mediacore.qos.LoadInfo))(loadInfo) | Le téléchargement d’un fragment a réussi. |
| [onOperationFailed](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html)(MediaPlayerNotification). [Avertissement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) ) | Une erreur récupérable s&#39;est produite. |
| [onSeekComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekComplete(long))(long ajustedTime) | La recherche est terminée. |
| [onSeekStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekStart()) | La recherche commence. |