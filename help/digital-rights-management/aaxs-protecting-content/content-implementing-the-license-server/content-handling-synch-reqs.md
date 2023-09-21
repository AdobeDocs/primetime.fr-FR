---
title: Gestion des requêtes de synchronisation
description: Gestion des requêtes de synchronisation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Gestion des requêtes de synchronisation{#handling-synchronization-requests}

. Si une licence spécifie des exigences de synchronisation ([Conditions requises pour la synchronisation](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-time-based-rules/content-time-based-rules-defining.md#requirements-for-synchronization)), le client enverra régulièrement des demandes de synchronisation au serveur, selon la fréquence spécifiée dans la licence. Pour activer les messages de synchronisation, définissez SyncFrequencyRequirements dans un PlayRight.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* La classe de message de requête est `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Si le protocole de prise en charge du client et du serveur version 5, l’URL de demande est &quot;URL du serveur de licences dans les métadonnées : + &quot;/flashaccess/sync/v4&quot;. Sinon, l’URL de demande est &quot;URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/sync/v3&quot;

Les messages de synchronisation sont utilisés pour synchroniser l’heure du client avec celle du serveur. Si des licences sont incorporées dans le contenu et n’ont pas besoin d’être récupérées à partir d’un serveur de licences, il est important de synchroniser l’heure du client pour empêcher le client de modifier son horloge afin de contourner l’expiration de licence.

Les messages de synchronisation peuvent également être utilisés pour communiquer les informations d’état du client au serveur ( `getClientState()`) pour la détection de restauration. Voir [Protection de restauration](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-rollback-detection.md).
