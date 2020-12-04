---
description: TVSDK distribue des événements de lecture publicitaire en réponse à des opérations liées à la publicité, telles que le début de la lecture d’une publicité.
seo-description: TVSDK distribue des événements de lecture publicitaire en réponse à des opérations liées à la publicité, telles que le début de la lecture d’une publicité.
seo-title: Événements de lecture des publicités
title: Événements de lecture des publicités
uuid: dd6991ae-3e33-4d92-92e9-26b1086a555a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---


# Événements de lecture de publicité {#ad-playback-events}

TVSDK distribue des événements de lecture publicitaire en réponse à des opérations liées à la publicité, telles que le début de la lecture d’une publicité.

Pour être averti de tous les événements liés à la lecture de publicités, enregistrez une implémentation de `MediaPlayer.AdPlaybackEventListener`, y compris les rappels suivants.

>[!TIP]
>
>Lorsque des publicités sont insérées ou supprimées du média, TVSDK distribue le événement de lecture [onTimelineUpdate](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated()).

| Événement | Signification |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak))  (AdBreak adBreak) | Une coupure publicitaire s’est complètement déroulée. |
| onAdBreakSkipped | Une coupure publicitaire a été ignorée pendant la lecture. |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak))  (AdBreak adBreak) | Une coupure publicitaire a commencé. |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak adBreak, AdBreak, AdClick adClick) | L&#39;utilisateur a cliqué sur la publicité. Fournit des informations à votre application sur la publicité sur laquelle l’utilisateur a cliqué, en réponse à votre application qui appelait `notifyClick` sur le `MediaPlayerView`. |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak))  (AdBreak adBreak, publicité) | Une publicité a été complètement lue. |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int))  (AdBreak adBreak, publicité, pourcentage int) | La lecture de la publicité a progressé. Distribué plusieurs fois pendant la lecture d’une publicité. |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad))  (AdBreak adBreak, publicité) | Une publicité a commencé. |