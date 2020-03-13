---
description: 'Vous devez vous assurer de délivrer des licences en toute sécurité. Tenez compte de ces bonnes pratiques pour protéger le serveur de licences '
seo-description: 'Vous devez vous assurer de délivrer des licences en toute sécurité. Tenez compte de ces bonnes pratiques pour protéger le serveur de licences '
seo-title: Protection du serveur de licences
title: Protection du serveur de licences
uuid: 7b5de17d-d0a7-41df-9651-4ff51c9965c6
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Protection du serveur de licences {#protecting-the-license-server}

Vous devez vous assurer de délivrer des licences en toute sécurité. Tenez compte des bonnes pratiques suivantes pour protéger le serveur de licences :

## Consommation de listes CRL générées localement {#consuming-locally-generated-crls}

Pour utiliser les  de révocation des certificats (CRL) générées localement et les de mise à jour des stratégies, utilisez les API DRM d’Adobe Primetime pour vérifier la signature.

Les API suivantes vérifient que le  du n’a pas été modifié et que le  a été signé par le serveur de licence approprié :

* Appelez [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir la [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) à toute API.

   Pour plus d’informations, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Appelez [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir le `PolicyUpdateList` à toute API.

   Pour plus d’informations, voir [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

## Consommation de listes CRL publiées par Adobe{#consuming-crls-published-by-adobe}

Le SDK télécharge régulièrement les listes CRL publiées par Adobe. Vous devez vous assurer que l’accès à ces fichiers n’est pas bloqué ou que l’application de ces listes CRL n’est pas empêchée.

Le kit SDK dispose d’une option de configuration permettant d’ignorer les erreurs lors de la récupération des listes CRL Adobe. Vous ne pouvez l’appliquer que dans les  de développement . Dans le  de production , le serveur de licences doit récupérer les listes CRL auprès d’Adobe. Si le serveur de licences ne parvient pas à obtenir une liste CRL valide, une erreur s’est produite.

## Génération de listes CRL pour compléter celles publiées par Adobe{#generating-crls-to-supplement-those-published-by-adobe}

Vous pouvez utiliser Adobe Primetime DRM pour créer des listes CRL qui complètent la liste CRL de l’ordinateur publiée par Adobe.

Le SDK DRM Primetime vérifie et applique les listes CRL Adobe. Cependant, vous pouvez interdire d’autres ordinateurs clients en créant une liste CRL qui révoque des informations d’identification supplémentaires en transmettant la liste CRL au SDK DRM Primetime. Lorsque vous émettez une licence, le SDK vérifie la liste de révocation des certificats Adobe et votre liste de révocation des certificats.

Pour générer des listes CRL, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

## Détection de restauration {#rollback-detection}

Si votre implémentation d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de la fenêtre de lecture), Adobe recommande que le serveur effectue le suivi du compteur d’annulation et utilise la liste blanche AIR ou SWF.

Le compteur de restauration est envoyé au serveur dans la plupart des requêtes du client. Si votre implémentation de DRM Primetime ne nécessite pas le compteur de restauration, elle peut être ignorée. Dans le cas contraire, Adobe recommande au serveur de stocker l’ID d’ordinateur aléatoire, obtenu à l’aide de [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()), et la valeur actuelle du compteur dans une base de données.

Pour plus d’informations sur la manière d’incrémenter et de suivre le compteur d’annulation, voir [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) et détection de restauration.

## Nombre d’ordinateurs lors de l’émission des licences {#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent que le nombre d’ordinateurs d’un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les ID d’ordinateur associés à l’utilisateur.

La méthode la plus efficace pour suivre les ID d’ordinateur consiste à stocker la valeur renvoyée par la méthode [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) dans une base de données. Lorsqu’une nouvelle requête est reçue, comparez l’ID d’ordinateur de la requête aux ID d’ordinateur connus à l’aide de [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) effectue une comparaison des ID pour déterminer si les ID représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’ID d’ordinateur. Par exemple, si les utilisateurs sont autorisés à utiliser cinq ordinateurs dans leur domaine, vous pouvez rechercher dans la base de données les ID d’ordinateur associés au nom d’utilisateur de l’utilisateur et obtenir un petit jeu de données à des fins de comparaison.

Cette comparaison n’est pas pratique pour les déploiements qui autorisent un accès anonyme. Dans ce cas, [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) peut être utilisé. Toutefois, cet ID ne peut pas être identique si l’utilisateur accède au contenu à partir des moteurs d’exécution Flash et Adobe AIR®.

>[!NOTE]
>
>L’ID ne survit pas si l’utilisateur reformate le disque dur.

## Protection de relecture {#replay-protection}

La protection Replay empêche un attaquant de lire à nouveau un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client.

Une attaque par déni de service est une tentative de la part d’attaquants visant à empêcher les utilisateurs légitimes d’un service d’utiliser ce service. Par exemple, une attaque de relecture qui utilise le compteur d’annulation peut être utilisée pour &quot;tromper&quot; le serveur de licences en pensant que le client DRM a annulé son état, ce qui entraîne une suspension du compte.

Pour en savoir plus sur la protection de relecture, voir [ AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).

## Tenir à jour une liste blanche des gestionnaires de contenu approuvés{#maintain-a-whitelist-of-trusted-content-packagers}

Une liste blanche est un d’entités de confiance.

Pour les gestionnaires de contenu, les entités sont des organisations auxquelles le propriétaire du contenu fait confiance pour assembler (ou chiffrer) les fichiers vidéo et créer du contenu protégé DRM. Lors du déploiement d’Adobe Primetime DRM, vous devez conserver une liste blanche des gestionnaires de contenu approuvés. Vous devez également vérifier l’identité du gestionnaire de contenu dans les métadonnées DRM d’un fichier protégé DRM avant d’émettre une licence.

Pour savoir comment obtenir des informations sur l’entité qui a compressé le contenu, voir [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).

## Délai d’expiration pour les jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK DRM d’Adobe Primetime ont un délai d’expiration pour protéger la sécurité de l’application.

L’expiration du jeton d’authentification est spécifiée à l’aide du SDK DRM Primetime lors du traitement d’une demande d’authentification. Une fois arrivé à expiration, le jeton n’est plus valide et l’utilisateur doit s’authentifier à nouveau auprès du serveur de licences.

Pour en savoir plus sur les demandes d’authentification, voir [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).

## Remplacement des options de stratégie {#overriding-policy-options}

Lorsque vous émettez une licence, le serveur de licences peut remplacer les règles d’utilisation spécifiées dans la stratégie.

Si la stratégie spécifie une date de , aucune licence n’est générée avant cette date  de. Cependant, vous pouvez définir une date de  future dans la licence une fois la licence générée. Cette option doit être utilisée avec précaution car le client ne peut pas empêcher l’utilisateur de faire avancer le temps du système pour contourner la date de  du.