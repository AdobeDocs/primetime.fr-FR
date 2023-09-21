---
title: Protection des relecture
description: Protection des relecture
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Protection des relecture{#replay-protection}

Pour la protection de relecture, il peut être prudent de vérifier si l’identifiant du message a été vu récemment en appelant `RequestMessageBase.getMessageId()`. Si tel est le cas, un attaquant peut essayer de relayer la requête, ce qui doit être refusé. Pour détecter les tentatives de relecture, le serveur peut stocker une liste d’identifiants de message récemment consultés et comparer chaque requête entrante à la liste mise en cache. Pour limiter la durée de stockage des identifiants de message, appelez `HandlerConfiguration.setTimestampTolerance()`. Si cette propriété est définie, le SDK refuse toute demande qui comporte un horodatage supérieur au nombre de secondes spécifié de l’heure du serveur.
