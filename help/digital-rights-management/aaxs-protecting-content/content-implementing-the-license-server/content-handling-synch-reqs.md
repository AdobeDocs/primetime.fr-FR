---
seo-title: Gestion des demandes de synchronisation
title: Gestion des demandes de synchronisation
uuid: 37b2db09-4c09-4216-874b-b570a84569b6
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Gestion des demandes de synchronisation{#handling-synchronization-requests}

. Si une licence spécifie des exigences de synchronisation ([Conditions requises pour la synchronisation](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-time-based-rules/content-time-based-rules-defining.md#requirements-for-synchronization)), le client envoie régulièrement des demandes de synchronisation au serveur, selon la fréquence spécifiée dans la licence. Pour activer les messages de synchronisation, définissez SyncFrequencyRequirements dans un PlayRight.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de requête est &quot;URL du serveur de licence dans les métadonnées : + &quot;/flashaccess/sync/v4&quot;. Sinon, l’URL de requête est &quot;URL du serveur de licence dans les métadonnées&quot; + &quot;/flashaccess/sync/v3&quot;

Les messages de synchronisation sont utilisés pour synchroniser l’heure du client avec l’heure du serveur. Si des licences sont incorporées dans le contenu et qu’elles n’ont pas besoin d’être récupérées sur un serveur de licences, il est important de synchroniser l’heure du client pour empêcher ce dernier de modifier son horloge afin de contourner l’expiration de la licence.

Les messages de synchronisation peuvent également être utilisés pour communiquer les informations sur l’état du client au serveur ( `getClientState()`) à des fins de détection de restauration. Voir Protection [de restauration](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-rollback-detection.md).