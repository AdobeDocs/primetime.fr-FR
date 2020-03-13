---
description: TVSDK distribue des  de lecture publicitaire en réponse à des opérations liées aux publicités, telles qu’une  de lecture d’un publicitaire.
seo-description: TVSDK distribue des  de lecture publicitaire en réponse à des opérations liées aux publicités, telles qu’une  de lecture d’un publicitaire.
seo-title: 'de lecture de publicité '
title: 'de lecture de publicité '
uuid: 63138237-2315-45ff-914d-369da18fdff7
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# de lecture de publicité {#ad-playback-events}

TVSDK distribue des  de lecture publicitaire en réponse à des opérations liées aux publicités, telles qu’une  de lecture d’un publicitaire.

Pour être averti de tous les liés à la lecture de publicités, enregistrez les écouteurs avec l’ `MediaPlayer` objet pour le  suivant.

>[!TIP]
>
>Lorsque des publicités sont insérées ou supprimées du média, TVSDK distribue le de lecture  TimelineEvent.[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| Event | Signification |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | Une coupure publicitaire s&#39;est complètement déroulée. |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | Une coupure publicitaire a été ignorée pendant la lecture. |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | Une coupure publicitaire a commencé. |
| AdClickEvent.[AD_CLICK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | L’utilisateur a cliqué sur la publicité. Fournit des informations à votre application au sujet de la publicité sur laquelle l’utilisateur a cliqué, en réponse à l’appel de votre application `notifyClick` sur le `MediaPlayerView`. |
| AdPlaybackEvent.[AD _TERMINE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | Une publicité s&#39;est complètement jouée. |
| AdPlaybackEvent.[AD_PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | La lecture de la publicité a progressé. Distribué plusieurs fois pendant la lecture d’une publicité. |
| AdPlaybackEvent.[AD_SEEK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Une recherche s&#39;est produite au-delà des limites d&#39;une publicité ou au sein d&#39;une publicité. |
| AdPlaybackEvent.[AD_start](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Une publicité a commencé. |