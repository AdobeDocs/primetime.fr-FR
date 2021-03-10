---
title: Protection de relecture
description: Protection de relecture
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Protection de relecture{#replay-protection}

La protection de relecture empêche un attaquant de relire un message de demande de licence et peut causer une attaque par déni de service (DoS) contre le client (Une attaque par déni de service *est une tentative d&#39;attaque par des attaquants pour empêcher les utilisateurs légitimes d&#39;un service d&#39;utiliser ce service.)* Par exemple, une attaque de relecture utilisant le compteur d&#39;annulation peut être utilisée pour &quot;tromper&quot; le serveur de licences afin de lui faire croire que le client DRM est en train de restaurer son état, ce qui entraîne la suspension du compte.

Pour en savoir plus sur la protection de relecture, voir `AbstractRequestMessage.getMessageId()` le *Guide de référence de l&#39;API d&#39;accès aux Adobes*.
