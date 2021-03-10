---
title: Révocation des informations d’identification du client et de l’exécution DRM
description: Révocation des informations d’identification du client et de l’exécution DRM
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---


# Révocation des informations d’identification du client et de l’exécution DRM {#revoking-drm-client-and-runtime-credentials}

Les versions DRM/Runtime sont identifiées par le niveau de sécurité, le numéro de version et d&#39;autres attributs, y compris le système d&#39;exploitation et l&#39;exécution. Pour limiter les versions DRM/Runtime autorisées, définissez les restrictions de module dans une stratégie DRM ou dans une `HandlerConfiguration`. Les restrictions de module peuvent inclure un niveau de sécurité minimum et la liste des versions de module qui ne sont pas autorisées à recevoir une licence.

Voir [Liste bloquée des clients DRM interdits d&#39;accès au contenu protégé](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blocklist-drm-clients.md) pour plus d&#39;informations sur les attributs utilisés pour identifier un module DRM/Runtime.

Si le niveau de sécurité minimum est défini, la version sur le client (spécifiée dans le jeton de l&#39;ordinateur) doit être supérieure ou égale à la valeur spécifiée.

Si une liste de versions exclues est spécifiée et que la version du client correspond à l’un des identifiants de version de la liste, le client n’est pas autorisé à utiliser un droit contenant cette instance ModuleRequirements. Pour qu&#39;un module corresponde aux informations de version, tous les paramètres spécifiés dans les informations de version, à l&#39;exception de la version de publication, doivent correspondre exactement aux valeurs des modules. La version de publication correspond si la valeur du module client est inférieure ou égale à la valeur des informations de version.

Dans le événement où une violation est signalée avec un client DRM ou une version d’exécution particulier, le propriétaire du contenu et le diffuseur de contenu (qui exécute le serveur de licences) peuvent configurer le serveur pour qu’il refuse d’émettre des licences pendant une période pendant laquelle l’Adobe ne dispose pas de correctif. Ceci peut être configuré par l&#39;intermédiaire de `HandlerConfiguration` comme décrit ci-dessus, ou en apportant des modifications à toutes les stratégies DRM. Dans ce dernier cas, vous pouvez conserver une liste de mise à jour de stratégie DRM et l&#39;utiliser pour vérifier si une stratégie DRM a été mise à jour ou révoquée.

Si vous avez besoin d’une version plus récente de l’exécution Adobe Flash Player/Adobe AIR ou de la bibliothèque DRM (Adobe Content Protection Library), vous devez mettre à jour vos stratégies DRM.

Voir [Mise à jour d’une stratégie à l’aide de l’API Java](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md).

Ensuite, vous devez créer une Liste de mise à jour de stratégie DRM ou définir des restrictions dans `HandlerConfiguration` en appelant `HandlerConfiguration.setRuntimeModuleRequirements()` ou `HandlerConfiguration.setDRMModuleRequirements()`. Lorsqu’un utilisateur demande une nouvelle licence avec les listes bloquées spécifiées activées, vous devez installer les derniers runtimes et bibliothèques avant de pouvoir émettre une licence.

Voir l&#39;exemple de code dans [Mise à jour d&#39;une stratégie à l&#39;aide de l&#39;API Java Pour obtenir un exemple sur la liste des blocs DRM et les versions d&#39;exécution](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md), reportez-vous à la section relative à la liste des blocs DRM et aux versions d&#39;exécution.
