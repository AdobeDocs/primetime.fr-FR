---
description: Les  de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, l’achèvement des actions que vous avez demandées, comme le démarrage de la lecture d’une vidéo, ou les actions qui se produisent implicitement, comme l’achèvement d’une publicité.
seo-description: Les  de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, l’achèvement des actions que vous avez demandées, comme le démarrage de la lecture d’une vidéo, ou les actions qui se produisent implicitement, comme l’achèvement d’une publicité.
seo-title: 'Écoute du de Primetime Player '
title: 'Écoute du de Primetime Player '
uuid: f85cf9aa-50a1-4b06-a2fe-6b20f84cff32
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Présentation {#listen-for-primetime-player-events-overview}

Les  de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, l’achèvement des actions que vous avez demandées, comme le démarrage de la lecture d’une vidéo, ou les actions qui se produisent implicitement, comme l’achèvement d’une publicité.

Comme votre application doit répondre à un grand nombre de ces  de, vous devez mettre en oeuvre des routines de gestion des  de et enregistrer ces routines avec TVSDK. Les routines appellent les méthodes TVSDK appropriées pour répondre de manière appropriée.

Voici quelques informations supplémentaires sur les  de :

* La nature en temps réel de la lecture vidéo nécessite un asynchrone (non bloquant)  pour de nombreuses opérations TVSDK.
* TVSDK prend en charge un lecteur vidéo  piloté par un.

   Il fournit des  qui correspondent à toutes les étapes importantes du processus de lecture. Vous enregistrez ces  avec le mécanisme de de votre plate-forme et créez des gestionnaires de qui seront appelés lors de l’apparition de ces. *`Event Handlers`* sont également connues sous le nom de routines de rappel ou d’écouteurs . TVSDK fournit une gamme complète de méthodes qui peuvent être utilisées par les gestionnaires de  de.
* En règle générale, votre application déclenche des opérations non bloquantes, telles que la demande de lecture d’un vidéo .

   TVSDK communique de manière asynchrone avec votre application en distribuant des , par exemple lorsque le vidéo  la lecture et un  lorsque la vidéo se termine. D’autres  peuvent indiquer des changements d’état dans votre lecteur et des conditions d’erreur. Les gestionnaires de vos  prennent les mesures appropriées.

