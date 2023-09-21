---
title: Révocation des informations d’identification du client et de l’exécution DRM
description: Révocation des informations d’identification du client et de l’exécution DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Révocation des informations d’identification du client et de l’exécution DRM {#revoking-drm-client-and-runtime-credentials}

Les versions DRM/Runtime sont identifiées par le niveau de sécurité, le numéro de version et d’autres attributs, y compris le système d’exploitation et le runtime. Pour restreindre les versions DRM/Runtime autorisées, définissez les restrictions de module dans une stratégie DRM ou dans une `HandlerConfiguration`. Les restrictions des modules peuvent inclure un niveau de sécurité minimal et la liste des versions de module qui ne sont pas autorisées à recevoir une licence.

Voir [Liste bloquée des clients DRM limitée à l’accès au contenu protégé](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blocklist-drm-clients.md) pour plus d’informations sur les attributs utilisés pour identifier un module DRM/Runtime.

Si le niveau de sécurité minimum est défini, la version du client (spécifiée dans le jeton de la machine) doit être supérieure ou égale à la valeur spécifiée.

Si une liste de versions exclues est spécifiée et que la version du client correspond à l’un des identifiants de version de la liste, le client ne sera pas autorisé à utiliser un droit contenant cette instance ModuleRequirements. Pour qu’un module corresponde aux informations de version, tous les paramètres spécifiés dans les informations de version, à l’exception de la version de publication, doivent correspondre exactement aux valeurs des modules. La version de publication correspond si la valeur du module client est inférieure ou égale à la valeur dans les informations de version.

Dans le cas où une violation est signalée avec un client DRM ou une version d’exécution spécifique, le propriétaire du contenu et le répartiteur de contenu (qui exécute le serveur de licences) peuvent configurer le serveur pour refuser d’émettre des licences pendant une période pendant laquelle l’Adobe n’a pas de correctif disponible. Vous pouvez le configurer via l’option `HandlerConfiguration` comme décrit ci-dessus ou en apportant des modifications à toutes les stratégies DRM. Dans ce dernier cas, vous pouvez gérer une liste de mise à jour de stratégie DRM et l’utiliser pour vérifier si une stratégie DRM a été mise à jour ou révoquée.

Si vous avez besoin d’une version plus récente de Adobe Flash Player/Adobe AIR Runtime ou de la bibliothèque Adobe de protection du contenu (module DRM), vous devez mettre à jour vos stratégies DRM.

Voir [Mise à jour d’une stratégie à l’aide de l’API Java](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md).

Vous devez ensuite créer une liste de mise à jour de stratégie DRM ou définir des restrictions dans `HandlerConfiguration` en appelant `HandlerConfiguration.setRuntimeModuleRequirements()` ou `HandlerConfiguration.setDRMModuleRequirements()`. Lorsqu’un utilisateur demande une nouvelle licence avec les listes bloquées spécifiées activées, vous devez installer les derniers runtime et bibliothèques avant qu’une licence puisse être émise.

Voir l’exemple de code dans [Mise à jour d’une stratégie à l’aide de l’API Java Exemple de mise en liste bloquée des versions DRM et d’exécution](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) pour obtenir un exemple sur la liste bloquée des versions DRM et runtime.
