---
description: TVSDK distribue des événements de lecture de publicité en réponse à des opérations liées à la publicité, telles que lorsqu’une publicité commence à être lue.
title: Événements de lecture de publicité
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Événements de lecture de publicité {#ad-playback-events}

TVSDK distribue des événements de lecture de publicité en réponse à des opérations liées à la publicité, telles que lorsqu’une publicité commence à être lue.

Pour être averti de tous les événements liés à la lecture de la publicité, enregistrez les écouteurs auprès de la fonction `MediaPlayer` pour les événements suivants.

>[!TIP]
>
>Lorsque des publicités sont insérées dans le média ou supprimées, TVSDK distribue l’événement de lecture TimelineEvent.[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| Événement | Signification |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | Une coupure publicitaire s’est complètement déroulée. |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | Une coupure publicitaire a été ignorée pendant la lecture. |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | Une coupure publicitaire a commencé. |
| AdClickEvent.[AD_CLICK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | L’utilisateur a cliqué sur la publicité. Fournit des informations à votre application sur la publicité sur laquelle l’utilisateur a cliqué, en réponse à l’appel de votre application. `notifyClick` sur le `MediaPlayerView`. |
| AdPlaybackEvent.[AD_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | Une publicité s&#39;est complètement jouée. |
| AdPlaybackEvent.[AD_PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | La lecture de la publicité a progressé. Distribué plusieurs fois pendant la lecture d’une publicité. |
| AdPlaybackEvent.[AD_SEEK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Une recherche s’est produite au-delà des limites d’une publicité ou au sein d’une publicité. |
| AdPlaybackEvent.[AD_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Une publicité a commencé. |
