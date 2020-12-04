---
description: Les événements du navigateur TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
seo-description: Les événements du navigateur TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
seo-title: Écoute des événements du lecteur Primetime
title: Écoute des événements du lecteur Primetime
uuid: 7b7c28ac-22ae-46a3-bbeb-bef1b04baeb3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Aperçu {#listen-for-primetime-player-events-overview}

Les événements du navigateur TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.

Comme votre application doit répondre à un grand nombre de ces événements, vous devez mettre en oeuvre des routines de gestion de événement et enregistrer ces routines avec le navigateur TVSDK. Les routines appellent les méthodes appropriées du navigateur TVSDK pour répondre de manière appropriée.

Voici quelques informations supplémentaires sur les événements :

* La nature en temps réel de la lecture vidéo requiert une activité asynchrone (non bloquée) pour de nombreuses opérations du navigateur TVSDK.
* Le navigateur TVSDK prend en charge un lecteur vidéo piloté par événement.

   Il fournit des événements qui correspondent à toutes les étapes importantes du processus de lecture. Vous enregistrez ces événements avec le mécanisme de événement de votre plateforme et créez des gestionnaires de événements qui seront appelés lorsque ces événements se produiront. *`Event Handlers`* sont également connues sous le nom de routines de rappel ou d’écouteurs de événement. Le navigateur TVSDK fournit une gamme complète de méthodes qui peuvent être utilisées par les gestionnaires de événement.
* En règle générale, votre application lance des opérations non bloquantes, telles que la demande de lecture d’un début vidéo.

   Le navigateur TVSDK communique de manière asynchrone avec votre application en distribuant des événements, par exemple lorsque la lecture des débuts vidéo est terminée et un événement lorsque la vidéo se termine. D’autres événements peuvent indiquer des changements d’état dans votre lecteur et des conditions d’erreur. Les gestionnaires de événement prennent les mesures appropriées.

