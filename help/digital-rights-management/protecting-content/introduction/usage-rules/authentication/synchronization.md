---
title: Conditions requises pour la synchronisation
description: Conditions requises pour la synchronisation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Conditions requises pour la synchronisation {#requirements-for-synchronization}

Conditions requises pour la synchronisation spécifie la fréquence à laquelle le client synchronise son état avec le serveur. Si le client a reçu une licence hors-bande (sans contact avec un serveur de licences), les règles d’utilisation peuvent spécifier que le client doit envoyer des messages de synchronisation au serveur afin de synchroniser l’heure sécurisée du client et de signaler l’état du client au serveur.

Le comportement de synchronisation est défini à l&#39;aide des paramètres suivants :

* **Intervalle de début** - Indique la durée d’attente après la dernière synchronisation réussie pour démarrer une autre requête de synchronisation.
* **Intervalle de fin hard** - (facultatif). Interdire la lecture si une synchronisation réussie ne s’est pas produite pendant la durée spécifiée.
* **Forcer la probabilité de synchronisation** - (facultatif). Probabilité avec laquelle le client doit envoyer un message de synchronisation avant l’intervalle de démarrage suivant.

>[!NOTE]
>
>Cette règle d’utilisation est prise en charge par les clients DRM Primetime version 3.0 ou ultérieure. Le comportement sur les clients plus anciens dépend de la version client minimale prise en charge par le serveur de licences.
