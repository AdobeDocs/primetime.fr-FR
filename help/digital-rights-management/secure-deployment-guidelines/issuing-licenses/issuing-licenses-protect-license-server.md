---
description: Vous devez vous assurer d’émettre des licences en toute sécurité. Tenez compte de ces bonnes pratiques pour protéger le serveur de licences
title: Protection du serveur de licences
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 0%

---

# Protection du serveur de licences {#protecting-the-license-server}

Vous devez vous assurer d’émettre des licences en toute sécurité. Tenez compte des bonnes pratiques suivantes pour protéger le serveur de licences :

## Consommation de listes CRL générées localement {#consuming-locally-generated-crls}

Pour utiliser des listes de révocation des certificats (CRL) générées localement et des listes de mise à jour de stratégie, utilisez les API DRM Adobe Primetime pour vérifier la signature.

Les API suivantes vérifient que les listes n’ont pas été modifiées et que les listes ont été signées par le bon serveur de licences :

* Appeler [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir l’événement [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) à toute API.

  Pour plus d’informations, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Appeler [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir l’événement `PolicyUpdateList` à toute API.

  Pour plus d’informations, voir [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

## Consommation de listes CRL publiées par Adobe{#consuming-crls-published-by-adobe}

Le SDK télécharge régulièrement les listes CRL publiées par Adobe. Vous devez vous assurer que l’accès à ces fichiers n’est pas bloqué ou que l’application de ces listes CRL n’est pas empêchée.

Le SDK dispose d’une option de configuration pour ignorer les erreurs lors de la récupération des listes CRL d’Adobe. Vous ne pouvez appliquer cette option que dans les environnements de développement. Dans les environnements de production, le serveur de licences doit récupérer les CRL d’Adobe. Si le serveur de licences ne parvient pas à obtenir une liste de révocation des certificats valide, une erreur s’est produite.

## Génération de listes CRL pour compléter celles publiées par Adobe{#generating-crls-to-supplement-those-published-by-adobe}

Vous pouvez utiliser Adobe Primetime DRM pour créer des CRL qui complètent la CRL de la machine publiée par Adobe.

Le SDK DRM Primetime vérifie et applique les listes CRL d’Adobe. Cependant, vous pouvez interdire d’autres ordinateurs clients en créant une liste de révocation des identifiants de machine supplémentaire en transmettant la liste de révocation des certificats au SDK DRM Primetime. Lorsque vous émettez une licence, le SDK vérifie la CRL d’Adobe et la CRL.

Pour générer des listes CRL, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

## Détection de restauration {#rollback-detection}

Si votre mise en oeuvre d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de temps de lecture), Adobe recommande que le serveur effectue le suivi du compteur de restauration et utilise les listes autorisées AIR ou SWF.

Le compteur de restauration est envoyé au serveur dans la plupart des requêtes du client. Si votre mise en oeuvre de Primetime DRM ne nécessite pas de compteur de restauration, elle peut être ignorée. Sinon, Adobe recommande que le serveur stocke l’identifiant aléatoire de la machine, obtenu à l’aide de [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())et la valeur actuelle du compteur dans une base de données.

Pour plus d’informations sur l’incrémentation et le suivi du compteur de restauration, voir [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) et Détection de restauration.

## Nombre de machines lors de l’émission de licences {#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent que le nombre de machines pour un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les identifiants de machines associés à l’utilisateur.

La méthode la plus robuste pour effectuer le suivi des ID d’ordinateur consiste à stocker la valeur renvoyée par la variable [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) dans une base de données. Lors de la réception d’une nouvelle requête, comparez l’identifiant de l’ordinateur dans la requête aux identifiants d’ordinateur connus en utilisant [MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) compare les identifiants pour déterminer si les identifiants représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’identifiants d’ordinateur. Si, par exemple, cinq machines de leur domaine sont autorisées pour les utilisateurs, vous pouvez rechercher dans la base de données les identifiants de machines associés au nom d’utilisateur de l’utilisateur et obtenir un petit ensemble de données à des fins de comparaison.

Cette comparaison n’est pas pratique pour les déploiements qui autorisent un accès anonyme. Dans ce cas, [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) peut être utilisé. Cependant, cet identifiant ne peut pas être le même si l’utilisateur accède au contenu à partir des environnements d’exécution Flash et Adobe AIR®.

>[!NOTE]
>
>L’identifiant ne survit pas si l’utilisateur reformate le disque dur.

## Protection des relecture {#replay-protection}

La protection de relecture empêche un attaquant de lire à nouveau un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client.

Une attaque du DoS est une tentative des attaquants d&#39;empêcher les utilisateurs légitimes d&#39;un service d&#39;utiliser ce service. Par exemple, une attaque de relecture qui utilise le compteur de restauration peut être utilisée pour &quot;inciter&quot; le serveur de licences à penser que le client DRM a rétabli son état, ce qui entraîne une suspension du compte.

Pour en savoir plus sur la protection de relecture, voir [AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).

## Conserver une liste autorisée de packages de contenu approuvés {#maintain-a-allowlist-of-trusted-content-packagers}

Une liste autorisée est une liste d’entités de confiance.

Pour les fournisseurs de modules de contenu, les entités sont des organisations approuvées par le propriétaire du contenu pour compresser (ou chiffrer) les fichiers vidéo et créer du contenu protégé DRM. Lors du déploiement d’Adobe Primetime DRM, vous devez gérer une liste autorisée de fournisseurs de contenu approuvés. Vous devez également vérifier l’identité du module de contenu dans les métadonnées DRM d’un fichier protégé par DRM avant d’émettre une licence.

Pour savoir comment obtenir des informations sur l’entité qui a empaqueté le contenu, voir [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).

## Timeout des jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK Adobe Primetime DRM ont un délai d’expiration pour protéger la sécurité de l’application.

L’expiration du jeton d’authentification est spécifiée à l’aide du SDK DRM Primetime lors de la gestion d’une demande d’authentification. Une fois expiré, le jeton n’est plus valide et l’utilisateur doit s’authentifier à nouveau auprès du serveur de licences.

Pour en savoir plus sur les demandes d’authentification, voir [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).

## Remplacement des options de stratégie {#overriding-policy-options}

Lorsque vous émettez une licence, le serveur de licences peut remplacer les règles d’utilisation spécifiées dans la stratégie.

Si la stratégie spécifie une date de début, aucune licence n’est générée avant cette date de début. Cependant, vous pouvez définir une date de début ultérieure dans la licence une fois la licence générée. Cette option doit être utilisée avec précaution, car le client ne peut pas empêcher l’utilisateur de remonter le temps du système pour contourner la date de début.
