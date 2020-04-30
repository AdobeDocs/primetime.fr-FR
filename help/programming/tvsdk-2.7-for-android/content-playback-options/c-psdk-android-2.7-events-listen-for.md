---
description: Les Événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
seo-description: Les Événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
seo-title: Écoute des événements du lecteur Primetime
title: Écoute des événements du lecteur Primetime
uuid: bd0a428c-fa51-41a6-950a-9d6843c6e177
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Présentation {#listen-for-primetime-player-events-overview}

Les Événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.

Comme votre application doit répondre à un grand nombre de ces événements, vous devez mettre en oeuvre des routines de gestion de événement et enregistrer ces routines avec TVSDK. Les routines appellent les méthodes TVSDK appropriées pour répondre de manière appropriée.

Plus d&#39;informations sur les événements :

* La nature en temps réel de la lecture vidéo requiert une activité asynchrone (non bloquante) pour de nombreuses opérations TVSDK.
* TVSDK prend en charge un lecteur vidéo piloté par événement.

   Il fournit des événements qui correspondent à toutes les étapes importantes du processus de lecture. Vous enregistrez ces événements avec le mécanisme de événement de votre plateforme et créez des gestionnaires de événements qui seront appelés lorsque ces événements se produiront. *`Event Handlers`* sont également connues sous le nom de routines de rappel ou d’écouteurs de événement. TVSDK fournit une gamme complète de méthodes qui peuvent être utilisées par les gestionnaires de événement.
* En règle générale, votre application lance des opérations non bloquantes, telles que la demande de lecture d’un début vidéo.

   TVSDK communique de manière asynchrone avec votre application en distribuant des événements, par exemple lorsque la lecture de la vidéo se début et un événement lorsque la vidéo se termine. D’autres événements peuvent indiquer des changements d’état dans votre lecteur et des conditions d’erreur. Les gestionnaires de événement prennent les mesures appropriées.