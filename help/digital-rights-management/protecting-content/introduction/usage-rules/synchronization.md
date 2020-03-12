---
description: 'null'
seo-description: 'null'
seo-title: Conditions requises pour la synchronisation
title: Conditions requises pour la synchronisation
uuid: 594a4bb2-c042-4485-9cae-73b8f9f93d82
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Conditions requises pour la synchronisation {#requirements-for-synchronization}

Les conditions requises pour la synchronisation indiquent la fréquence à laquelle le client synchronise son état avec le serveur. Si le client a reçu une licence hors bande (sans contact avec un serveur de licences), les règles d’utilisation peuvent spécifier que le client doit envoyer des messages de synchronisation au serveur afin de synchroniser l’heure sécurisée du client et de signaler l’état du client au serveur.

Le comportement de synchronisation est défini à l’aide des paramètres suivants :

* **Intervalle** de  : indique le délai d&#39;attente après la dernière synchronisation réussie pour  une autre demande de synchronisation.
* **Intervalle** d’arrêt fixe - (facultatif). Interdire la lecture si une synchronisation réussie ne s’est pas produite pendant la durée spécifiée.
* **Forcer la probabilité** de synchronisation - (facultatif). Probabilité avec laquelle le client doit envoyer un message de synchronisation avant l’intervalle de  suivant.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Cette règle d’utilisation est prise en charge par les clients DRM Primetime version 3.0 ou ultérieure. Le comportement sur les anciens clients dépend de la version minimale du client prise en charge par le serveur de licences.

