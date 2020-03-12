---
description: TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de qualité de service (mise en mémoire tampon ou recherche, par exemple).
seo-description: TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de qualité de service (mise en mémoire tampon ou recherche, par exemple).
seo-title: ' QoS'
title: ' QoS'
uuid: fd657cf0-c6d4-4e9a-b212-7d09d483cae9
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


#  QoS{#qos-events}

TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de qualité de service (mise en mémoire tampon ou recherche, par exemple).

Pour être averti de tous les  de liés à la qualité de service, inscrivez les auditeurs de  à l’ `MediaPlayer` objet pour l’ suivante :

| Event | Signification |
|---|---|
| BufferEvent.[BUFFERING_END](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_END) | La mise en mémoire tampon est terminée. |
| BufferEvent.[BUFFERING_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_BEGIN) | La mise en mémoire tampon a commencé. |
| SeekEvent.[SEEK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_END) | La recherche est terminée. |
| SeekEvent.[SEEK_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_BEGIN) | La recherche commence. |
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDK a modifié la position de recherche en raison des politiques publicitaires actuelles. |

