---
description: TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques de la qualité de service (QoS), comme la mise en mémoire tampon ou la recherche.
seo-description: TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques de la qualité de service (QoS), comme la mise en mémoire tampon ou la recherche.
seo-title: Événements QoS
title: Événements QoS
uuid: fd657cf0-c6d4-4e9a-b212-7d09d483cae9
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Événements QoS{#qos-events}

TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques de la qualité de service (QoS), comme la mise en mémoire tampon ou la recherche.

Pour être averti de tous les événements liés à la qualité de service, enregistrez les auditeurs de événement avec l&#39;objet `MediaPlayer` pour les événements suivants :

| Événement | Signification |
|---|---|
| BufferEvent.[BUFFERING_END](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_END) | La mise en mémoire tampon est terminée. |
| BufferEvent.[BUFFERING_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_BEGIN) | La mise en mémoire tampon a commencé. |
| SeekEvent.[SEEK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_END) | La recherche est terminée. |
| SeekEvent.[SEEK_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_BEGIN) | La recherche commence. |
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDK a modifié la position de recherche en raison des politiques publicitaires actuelles. |

