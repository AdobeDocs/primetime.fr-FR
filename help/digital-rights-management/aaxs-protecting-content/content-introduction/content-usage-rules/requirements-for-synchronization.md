---
seo-title: Conditions requises pour la synchronisation
title: Conditions requises pour la synchronisation
uuid: 976a0ae1-bece-437e-b95b-6cd222525d13
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Conditions requises pour la synchronisation{#requirements-for-synchronization}

Indique la fréquence à laquelle le client synchronise son état avec le serveur. Si le client a reçu une licence hors bande (sans contact avec un serveur de licences), les règles d’utilisation peuvent spécifier que le client doit envoyer des messages de synchronisation au serveur afin de synchroniser l’heure sécurisée du client et de signaler l’état du client au serveur.

Le comportement de synchronisation est défini à l’aide des paramètres suivants :

* Intervalle de début : indique le délai d&#39;attente après la dernière synchronisation réussie pour début d&#39;une autre demande de synchronisation.
* Intervalle d’arrêt définitif — (facultatif). Interdire la lecture si une synchronisation réussie n’a pas eu lieu pendant la durée spécifiée.
* Forcer la probabilité de synchronisation — (facultatif). Probabilité avec laquelle le client doit envoyer un message de synchronisation avant l&#39;intervalle de début suivant.

>[!NOTE]
>
>Cette règle d&#39;utilisation est prise en charge par les clients Adobe Access version 3.0 et ultérieure. Le comportement des clients plus anciens dépend de la version minimale du client prise en charge par le serveur de licences. Voir [Version minimale du client](../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).

