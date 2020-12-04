---
description: 'Vous devez vous assurer d’émettre des licences en toute sécurité. Tenez compte de ces bonnes pratiques pour protéger le serveur de licences '
seo-description: 'Vous devez vous assurer d’émettre des licences en toute sécurité. Tenez compte de ces bonnes pratiques pour protéger le serveur de licences '
seo-title: Protection du serveur de licences
title: Protection du serveur de licences
uuid: 7b5de17d-d0a7-41df-9651-4ff51c9965c6
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---


# Protection du serveur de licences {#protecting-the-license-server}

Vous devez vous assurer d’émettre des licences en toute sécurité. Tenez compte des bonnes pratiques suivantes pour protéger le serveur de licences :

## Consommation de listes CRL générées localement {#consuming-locally-generated-crls}

Pour utiliser des listes de révocation des certificats générées localement et des listes de mise à jour des stratégies, utilisez les API Adobe Primetime DRM pour vérifier la signature.

Les API suivantes vérifient que les listes n’ont pas été modifiées et que les listes ont été signées par le serveur de licences approprié :

* Appelez [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir la [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) à toute API.

   Pour plus d’informations, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Appelez [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir `PolicyUpdateList` à toute API.

   Pour plus d&#39;informations, voir [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

## Consommation de listes CRL publiées par Adobe{#consuming-crls-published-by-adobe}

Le SDK télécharge régulièrement les listes CRL publiées par Adobe. Vous devez vous assurer que l’accès à ces fichiers n’est pas bloqué ou que l’application de ces listes CRL n’est pas empêchée.

Le SDK dispose d’une option de configuration permettant d’ignorer les erreurs lors de la récupération des listes CRL d’Adobe et vous ne pouvez appliquer cette option que dans les environnements de développement. Dans les environnements de production, le serveur de licences doit récupérer les listes CRL à partir de l’Adobe. Si le serveur de licences ne parvient pas à obtenir une liste de révocation des certificats valide, une erreur s’est produite.

## Génération de listes CRL pour compléter celles publiées par Adobe{#generating-crls-to-supplement-those-published-by-adobe}

Vous pouvez utiliser Adobe Primetime DRM pour créer des listes CRL qui complètent la liste CRL de l’ordinateur publiée par Adobe.

Le SDK DRM de Primetime vérifie et applique les CRL d’Adobe. Cependant, vous pouvez interdire d’autres ordinateurs clients en créant une liste CRL qui révoque des informations d’identification d’ordinateur supplémentaires en transmettant la liste CRL au SDK DRM de Primetime. Lorsque vous émettez une licence, le SDK vérifie la liste de révocation des certificats de l’Adobe et la liste de révocation des certificats.

Pour générer des listes CRL, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

## Détection de restauration {#rollback-detection}

Si votre implémentation de Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de lecture), l’Adobe recommande que le serveur garde le suivi du compteur d’annulation et utilise AIR ou SWF pour autoriser la mise en vente.

Le compteur d&#39;annulation est envoyé au serveur dans la plupart des requêtes du client. Si votre mise en oeuvre de Primetime DRM ne nécessite pas le compteur d’annulation, elle peut être ignorée. Dans le cas contraire, l’Adobe recommande au serveur de stocker l’ID d’ordinateur aléatoire, obtenu à l’aide de [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) et de la valeur de compteur actuelle dans une base de données.

Pour plus d&#39;informations sur la façon d&#39;incrémenter et de suivre le compteur d&#39;annulation, voir [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) et Détection de restauration.

## Nombre d&#39;ordinateurs lors de l&#39;émission de licences {#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent le suivi du nombre d&#39;ordinateurs d&#39;un utilisateur, le serveur de licences ou le serveur de domaines doit stocker les ID d&#39;ordinateur associés à l&#39;utilisateur.

La méthode la plus efficace pour suivre les ID d&#39;ordinateur consiste à stocker la valeur renvoyée par la méthode [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) dans une base de données. Lorsqu’une nouvelle demande est reçue, comparez l’ID d’ordinateur de la demande aux ID d’ordinateur connus en utilisant [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) effectue une comparaison des identifiants pour déterminer si les identifiants représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’ID d’ordinateur. Par exemple, si les utilisateurs sont autorisés à utiliser cinq machines de leur domaine, vous pouvez rechercher dans la base de données les ID d’ordinateurs associés au nom d’utilisateur de l’utilisateur et obtenir un petit ensemble de données à des fins de comparaison.

Cette comparaison n’est pas pratique pour les déploiements qui autorisent un accès anonyme. Dans ce cas, [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) peut être utilisé. Toutefois, cet ID ne peut pas être identique si l’utilisateur accède au contenu à partir des runtimes Flash et Adobe AIR®.

>[!NOTE]
>
>L&#39;ID ne survit pas si l&#39;utilisateur reformate le disque dur.

## Protection de relecture {#replay-protection}

La protection Replay empêche un attaquant de relire un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client.

Une attaque par déni de service est une tentative d’attaque par des attaquants visant à empêcher les utilisateurs légitimes d’un service d’utiliser ce service. Par exemple, une attaque de relecture qui utilise le compteur d&#39;annulation peut être utilisée pour &quot;tromper&quot; le serveur de licences en lui faisant croire que le client DRM a rétabli son état, ce qui entraîne une suspension du compte.

Pour en savoir plus sur la protection de relecture, voir [ AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).

## Tenir à jour une liste autorisée de gestionnaires de contenu approuvés {#maintain-a-allowlist-of-trusted-content-packagers}

Une liste autorisée est une liste d&#39;entités de confiance.

Pour les gestionnaires de packages de contenu, les entités sont des organisations dont le propriétaire du contenu fait confiance pour assembler (ou chiffrer) les fichiers vidéo et créer du contenu protégé DRM. Lors du déploiement de Adobe Primetime DRM, vous devez conserver une liste autorisée de gestionnaires de contenu approuvés. Vous devez également vérifier l’identité du gestionnaire de contenu dans les métadonnées DRM d’un fichier protégé par DRM avant d’émettre une licence.

Pour savoir comment obtenir des informations sur l’entité qui a conditionné le contenu, voir [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).

## Délai d’expiration pour les jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK DRM Adobe Primetime ont un délai d’expiration pour protéger la sécurité de l’application.

L’expiration du jeton d’authentification est spécifiée, utilisez le SDK DRM Primetime lors du traitement d’une demande d’authentification. Une fois arrivé à expiration, le jeton n’est plus valide et l’utilisateur doit s’authentifier de nouveau auprès du serveur de licences.

Pour en savoir plus sur les demandes d’authentification, voir [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).

## Remplacement des options de stratégie {#overriding-policy-options}

Lorsque vous émettez une licence, le serveur de licences peut remplacer les règles d’utilisation spécifiées dans la stratégie.

Si la stratégie spécifie une date de début, aucune licence n’est générée avant cette date de début. Cependant, vous pouvez définir une date de début ultérieure dans la licence une fois la licence générée. Cette option doit être utilisée avec précaution car le client ne peut pas empêcher l’utilisateur de faire avancer le temps du système pour contourner la date de début.