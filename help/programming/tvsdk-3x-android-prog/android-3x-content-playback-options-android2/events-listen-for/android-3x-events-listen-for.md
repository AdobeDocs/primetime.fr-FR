---
description: Les événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
seo-description: Les événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
seo-title: Écoute des événements du lecteur Primetime
title: Écoute des événements du lecteur Primetime
uuid: 3aa0979c-6141-4098-9f19-d5fe23192827
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Aperçu {#listen-for-primetime-player-events-overview}

Les événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.

Comme votre application doit répondre à un grand nombre de ces événements, vous devez mettre en oeuvre des routines de gestion de événement et enregistrer ces routines avec TVSDK. Les routines appellent les méthodes TVSDK appropriées pour répondre de manière appropriée.

Plus d&#39;informations sur les événements :

* La nature en temps réel de la lecture vidéo requiert une activité asynchrone (non bloquante) pour de nombreuses opérations TVSDK.
* TVSDK prend en charge un lecteur vidéo piloté par événement.

   Il fournit des événements qui correspondent à toutes les étapes importantes du processus de lecture. Vous enregistrez ces événements avec le mécanisme de événement de votre plateforme et créez des gestionnaires de événements qui seront appelés lorsque ces événements se produiront. *`Event Handlers`* sont également connues sous le nom de routines de rappel ou d’écouteurs de événement. TVSDK fournit une gamme complète de méthodes qui peuvent être utilisées par les gestionnaires de événement.
* En règle générale, votre application lance des opérations non bloquantes, telles que la demande de lecture d’un début vidéo.

   TVSDK communique de manière asynchrone avec votre application en distribuant des événements, par exemple lorsque la lecture de la vidéo se début et un événement lorsque la vidéo se termine. D’autres événements peuvent indiquer des changements d’état dans votre lecteur et des conditions d’erreur. Les gestionnaires de événement prennent les mesures appropriées.