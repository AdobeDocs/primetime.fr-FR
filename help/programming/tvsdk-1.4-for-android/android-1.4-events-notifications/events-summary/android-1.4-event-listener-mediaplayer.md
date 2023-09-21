---
description: TVSDK distribue des événements de lecture de publicité en réponse à des opérations liées à la publicité, telles que lorsqu’une publicité commence à être lue.
title: Événements de lecture de publicité
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Événements de lecture de publicité{#ad-playback-events}

TVSDK distribue des événements de lecture de publicité en réponse à des opérations liées à la publicité, telles que lorsqu’une publicité commence à être lue.

Pour être averti de tous les événements liés à la lecture de la publicité, enregistrez une mise en oeuvre de `MediaPlayer.AdPlaybackEventListener` y compris les rappels suivants.

>[!TIP]
>
>Lorsque des publicités sont insérées dans le média ou supprimées, TVSDK distribue l’événement de lecture. [onTimelineUpdated](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated()).

| Événement | Signification |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Une coupure publicitaire s’est complètement déroulée. |
| onAdBreakSkipped | Une coupure publicitaire a été ignorée pendant la lecture. |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Une coupure publicitaire a commencé. |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak adBreak, publicité publicitaire, AdClick adClick) | L’utilisateur a cliqué sur la publicité. Fournit des informations à votre application sur la publicité sur laquelle l’utilisateur a cliqué, en réponse à l’appel de votre application. `notifyClick` sur le `MediaPlayerView`. |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak, publicité) | Une publicité s&#39;est complètement jouée. |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int)) (AdBreak adBreak, publicité, pourcentage int) | La lecture de la publicité a progressé. Distribué plusieurs fois pendant la lecture d’une publicité. |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad)) (AdBreak adBreak, publicité) | Une publicité a commencé. |
