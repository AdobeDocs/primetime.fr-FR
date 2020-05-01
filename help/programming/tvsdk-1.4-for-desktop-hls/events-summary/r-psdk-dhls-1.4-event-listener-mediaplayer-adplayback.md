---
description: TVSDK distribue des événements de lecture publicitaire en réponse à des opérations liées à la publicité, telles que le début de la lecture d’une publicité.
seo-description: TVSDK distribue des événements de lecture publicitaire en réponse à des opérations liées à la publicité, telles que le début de la lecture d’une publicité.
seo-title: événements de lecture des publicités
title: événements de lecture des publicités
uuid: 63138237-2315-45ff-914d-369da18fdff7
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# événements de lecture des publicités {#ad-playback-events}

TVSDK distribue des événements de lecture publicitaire en réponse à des opérations liées à la publicité, telles que le début de la lecture d’une publicité.

Pour être averti de tous les événements liés à la lecture d’une publicité, enregistrez les écouteurs avec l’ `MediaPlayer` objet pour les événements suivants.

>[!TIP]
>
>Lorsque des publicités sont insérées ou supprimées du média, TVSDK distribue l’événement TimelineEvent du événement de lecture.[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| Événement | Signification |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | Une coupure publicitaire s’est complètement déroulée. |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | Une coupure publicitaire a été ignorée pendant la lecture. |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | Une coupure publicitaire a commencé. |
| AdClickEvent.[AD_CLICK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | L&#39;utilisateur a cliqué sur la publicité. Fournit des informations à votre application sur la publicité sur laquelle l’utilisateur a cliqué, en réponse à votre application qui appelait `notifyClick` sur le `MediaPlayerView`. |
| AdPlaybackEvent.[PUB _TERMINÉ](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | Une publicité a été complètement lue. |
| AdPlaybackEvent.[_PROGRESSION PUBLIQUE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | La lecture de la publicité a progressé. Distribué plusieurs fois pendant la lecture d’une publicité. |
| AdPlaybackEvent.[AD_SEEK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Une recherche s&#39;est produite au-delà des limites d&#39;une publicité ou au sein d&#39;une publicité. |
| AdPlaybackEvent.[_DÉMARRÉ DE LA PUBLICITÉ](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Une publicité a commencé. |