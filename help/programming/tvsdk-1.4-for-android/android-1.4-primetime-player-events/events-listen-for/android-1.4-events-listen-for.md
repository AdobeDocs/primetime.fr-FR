---
description: Les événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles que le démarrage de la lecture d’une vidéo ou les actions qui se produisent implicitement, telles qu’une fin de publicité.
title: Écoute des événements du lecteur Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Présentation {#listen-for-primetime-player-events-overview}

Les événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles que le démarrage de la lecture d’une vidéo ou les actions qui se produisent implicitement, telles qu’une fin de publicité.

Comme votre application doit répondre à la plupart de ces événements, vous devez mettre en oeuvre des routines de gestion des événements et enregistrer ces routines avec TVSDK. Les routines appellent les méthodes TVSDK appropriées pour répondre de manière appropriée.

Voici quelques informations supplémentaires sur les événements :

* La nature en temps réel de la lecture vidéo nécessite une activité asynchrone (non bloquante) pour de nombreuses opérations TVSDK.
* TVSDK prend en charge un lecteur vidéo piloté par un événement.

  Il fournit des événements qui correspondent à toutes les étapes importantes du processus de lecture. Vous enregistrez ces événements avec le mécanisme d’événement de votre plateforme et créez des gestionnaires d’événements qui seront appelés lorsque ces événements se produisent. *`Event Handlers`* sont également appelées routines de rappel ou écouteurs d’événement. TVSDK fournit une gamme complète de méthodes pouvant être utilisées par les gestionnaires d’événements.
* Votre application lance généralement des opérations non bloquantes, comme la demande de démarrage de la lecture d’une vidéo.

  TVSDK communique de manière asynchrone avec votre application en distribuant des événements, comme lorsque la lecture de la vidéo démarre et un événement lorsque la vidéo se termine. D’autres événements peuvent indiquer des modifications d’état dans votre lecteur et des conditions d’erreur. Les gestionnaires d’événements prennent les mesures appropriées.
