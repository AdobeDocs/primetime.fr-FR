---
description: Les  du navigateur TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, l’achèvement des actions demandées, comme le démarrage de la lecture d’une vidéo, ou les actions qui se produisent implicitement, comme l’achèvement d’une publicité.
seo-description: Les  du navigateur TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, l’achèvement des actions demandées, comme le démarrage de la lecture d’une vidéo, ou les actions qui se produisent implicitement, comme l’achèvement d’une publicité.
seo-title: 'Écoute du de Primetime Player '
title: 'Écoute du de Primetime Player '
uuid: 7b7c28ac-22ae-46a3-bbeb-bef1b04baeb3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#listen-for-primetime-player-events-overview}

Les  du navigateur TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, l’achèvement des actions demandées, comme le démarrage de la lecture d’une vidéo, ou les actions qui se produisent implicitement, comme l’achèvement d’une publicité.

Comme votre application doit répondre à un grand nombre de ces  de, vous devez mettre en oeuvre des routines de -handing et enregistrer ces routines avec le navigateur TVSDK. Les routines appellent les méthodes appropriées du navigateur TVSDK pour répondre de manière appropriée.

Voici quelques informations supplémentaires sur les  de :

* La nature en temps réel de la lecture vidéo nécessite un asynchrone (non bloquant)  pour de nombreuses opérations du navigateur TVSDK.
* Le navigateur TVSDK prend en charge un lecteur vidéo  piloté par un.

   Il fournit des  qui correspondent à toutes les étapes importantes du processus de lecture. Vous enregistrez ces  avec le mécanisme de de votre plate-forme et créez des gestionnaires de qui seront appelés lors de l’apparition de ces. *`Event Handlers`* sont également connues sous le nom de routines de rappel ou d’écouteurs . Le navigateur TVSDK fournit une gamme complète de méthodes qui peuvent être utilisées par les gestionnaires de  de.
* En règle générale, votre application déclenche des opérations non bloquantes, telles que la demande de lecture d’un vidéo .

   Le navigateur TVSDK communique de manière asynchrone avec votre application en distribuant des , par exemple lorsque le vidéo  la lecture et un  lorsque la vidéo se termine. D’autres  peuvent indiquer des changements d’état dans votre lecteur et des conditions d’erreur. Les gestionnaires de vos  prennent les mesures appropriées.

