---
seo-title: Gestion des demandes de synchronisation
title: Gestion des demandes de synchronisation
uuid: e2623afb-7a57-402d-a8a1-07bcf6324d41
translation-type: tm+mt
source-git-commit: eed2ed2512c2c462cd43637d83d80bf9a5c0d490

---


# Gestion des demandes de synchronisation {#handle-synchronization-requests}

Si une licence spécifie les [conditions de synchronisation requises pour la synchronisation,](../../protecting-content/introduction/usage-rules/authentication/synchronization.md) le client envoie régulièrement des demandes de synchronisation au serveur, en fonction de la fréquence spécifiée dans la licence. Pour activer les messages de synchronisation, définissez `SyncFrequencyRequirements` dans un PlayRight.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de requête est &quot;URL du serveur de licence dans les métadonnées : + &quot; [!DNL /flashaccess/sync/v4]&quot;. Sinon, l’URL de requête est &quot;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/sync/v3]&quot;

Les messages de synchronisation sont utilisés pour synchroniser l’heure du client avec l’heure du serveur. Si des licences sont incorporées dans le contenu et qu’elles n’ont pas besoin d’être récupérées sur un serveur de licences, il est important de synchroniser l’heure du client pour empêcher ce dernier de modifier son horloge afin de contourner l’expiration de la licence.

Les messages de synchronisation peuvent également être utilisés pour communiquer les informations sur l’état du client au serveur ( `getClientState()`) à des fins de détection de restauration.

Voir Protection [de restauration](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection).
