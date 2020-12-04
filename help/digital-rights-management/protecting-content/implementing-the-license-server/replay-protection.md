---
seo-title: Protection de relecture
title: Protection de relecture
uuid: c737998a-9c33-48b4-b741-91106697d71f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# Protection de relecture{#replay-protection}

Pour la protection de la relecture, vous pouvez vérifier si l&#39;identifiant du message a été vu récemment en appelant `RequestMessageBase.getMessageId()`. Si tel est le cas, un attaquant peut essayer de rejouer la requête, ce qui devrait être refusé. Pour détecter les tentatives de relecture, le serveur peut stocker une liste d’identifiants de message récemment vus et vérifier chaque requête entrante par rapport à la liste mise en cache. Pour limiter la durée de stockage des identificateurs de message, appelez `HandlerConfiguration.setTimestampTolerance()`. Si cette propriété est définie, le SDK refuse toute requête qui comporte un horodatage pendant plus de la durée spécifiée en secondes.
