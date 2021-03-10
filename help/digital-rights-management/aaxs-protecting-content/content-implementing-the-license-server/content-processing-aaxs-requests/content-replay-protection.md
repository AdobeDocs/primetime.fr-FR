---
title: Protection de relecture
description: Protection de relecture
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# Protection de relecture{#replay-protection}

Pour la protection de la relecture, il peut être prudent de vérifier si l&#39;identifiant du message a été vu récemment en appelant `RequestMessageBase.getMessageId()`. Si tel est le cas, un attaquant peut essayer de rejouer la requête, ce qui devrait être refusé. Pour détecter les tentatives de relecture, le serveur peut stocker une liste d’identifiants de message récemment vus et vérifier chaque requête entrante par rapport à la liste mise en cache. Pour limiter la durée de stockage des identificateurs de message, appelez `HandlerConfiguration.setTimestampTolerance()`. Si cette propriété est définie, le SDK refusera toute requête dont l’horodatage dépasse le nombre de secondes spécifié par rapport à l’heure du serveur.
