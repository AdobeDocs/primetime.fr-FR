---
title: Protection des relecture
description: Protection des relecture
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Protection des relecture{#replay-protection}

Pour la protection de relecture, vous pouvez vérifier si l’identifiant du message a été vu récemment en appelant `RequestMessageBase.getMessageId()`. Si tel est le cas, un attaquant peut essayer de relayer la requête, ce qui doit être refusé. Pour détecter les tentatives de relecture, le serveur peut stocker une liste d’identifiants de message récemment consultés et comparer chaque requête entrante à la liste mise en cache. Pour limiter la durée de stockage des identifiants de message, appelez `HandlerConfiguration.setTimestampTolerance()`. Si cette propriété est définie, le SDK refuse toute demande qui comporte un horodatage pendant plus de secondes de l’heure du serveur.
