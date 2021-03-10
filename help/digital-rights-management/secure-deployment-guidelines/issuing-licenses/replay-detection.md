---
description: La protection Replay empêche un attaquant de relire un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client.
title: Protection de relecture
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Protection de relecture{#replay-protection}

La protection Replay empêche un attaquant de relire un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client.

Une attaque par déni de service est une tentative d’attaque par des attaquants visant à empêcher les utilisateurs légitimes d’un service d’utiliser ce service. Par exemple, une attaque de relecture qui utilise le compteur d&#39;annulation peut être utilisée pour &quot;tromper&quot; le serveur de licences en lui faisant croire que le client DRM a rétabli son état, ce qui entraîne une suspension du compte.

Pour en savoir plus sur la protection de relecture, voir [ AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).
