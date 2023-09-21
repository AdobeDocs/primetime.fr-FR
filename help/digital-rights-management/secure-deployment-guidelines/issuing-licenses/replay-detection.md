---
description: La protection de relecture empêche un attaquant de lire à nouveau un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client.
title: Protection des relecture
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Protection des relecture{#replay-protection}

La protection de relecture empêche un attaquant de lire à nouveau un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client.

Une attaque du DoS est une tentative des attaquants d&#39;empêcher les utilisateurs légitimes d&#39;un service d&#39;utiliser ce service. Par exemple, une attaque de relecture qui utilise le compteur de restauration peut être utilisée pour &quot;inciter&quot; le serveur de licences à penser que le client DRM a rétabli son état, ce qui entraîne une suspension du compte.

Pour en savoir plus sur la protection de relecture, voir [AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).
