---
title: Protection des relecture
description: Protection des relecture
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Protection des relecture{#replay-protection}

La protection de relecture empêche un attaquant de lire à nouveau un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client (A *déni de service* L&#39;attaque est une tentative des attaquants d&#39;empêcher les utilisateurs légitimes d&#39;un service d&#39;utiliser ce service.) Par exemple, une attaque de relecture utilisant le compteur de restauration peut être utilisée pour &quot;inciter&quot; le serveur de licences à penser que le client DRM restaure son état, provoquant une suspension du compte.

Pour en savoir plus sur la protection de relecture, voir `AbstractRequestMessage.getMessageId()` la valeur *Référence de l’API Adobe Access*.
