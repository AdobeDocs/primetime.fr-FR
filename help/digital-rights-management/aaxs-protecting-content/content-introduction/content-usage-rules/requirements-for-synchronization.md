---
seo-title: Conditions requises pour la synchronisation
title: Conditions requises pour la synchronisation
uuid: 976a0ae1-bece-437e-b95b-6cd222525d13
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Conditions requises pour la synchronisation{#requirements-for-synchronization}

Indique la fréquence à laquelle le client synchronise son état avec le serveur. Si le client a reçu une licence hors bande (sans contact avec un serveur de licences), les règles d’utilisation peuvent spécifier que le client doit envoyer des messages de synchronisation au serveur afin de synchroniser l’heure sécurisée du client et de signaler l’état du client au serveur.

Le comportement de synchronisation est défini à l’aide des paramètres suivants :

* Intervalle  — Indique le délai d’attente après la dernière synchronisation réussie pour d’une autre requête de synchronisation.
* Intervalle d&#39;arrêt fixe — (Facultatif). Interdire la lecture si une synchronisation réussie ne s’est pas produite pendant la durée spécifiée.
* Forcer la probabilité de synchronisation — (Facultatif). Probabilité avec laquelle le client doit envoyer un message de synchronisation avant l’intervalle de  suivant.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Cette règle d’utilisation est prise en charge par les clients Adobe Access versions 3.0 et ultérieures. Le comportement sur les anciens clients dépend de la version minimale du client prise en charge par le serveur de licences. Voir Version [](../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md)minimale du client.

