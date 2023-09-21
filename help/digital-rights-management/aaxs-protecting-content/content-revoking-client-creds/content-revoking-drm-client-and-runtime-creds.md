---
title: Révocation des informations d’identification du client et de l’exécution DRM
description: Révocation des informations d’identification du client et de l’exécution DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Révocation des informations d’identification du client et de l’exécution DRM{#revoking-drm-client-and-runtime-credentials}

Les versions DRM/Runtime sont identifiées par le niveau de sécurité, le numéro de version et d’autres attributs, y compris le système d’exploitation et l’exécution. Pour restreindre les versions DRM/Runtime autorisées, définissez les restrictions du module dans une stratégie ou dans une `HandlerConfiguration`. Les restrictions des modules peuvent inclure un niveau de sécurité minimal et la liste des versions de module qui ne sont pas autorisées à recevoir une licence. Voir [Liste bloquée des clients DRM limitée à l’accès au contenu protégé](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-blocklist-drm-clients.md) pour plus d’informations sur les attributs utilisés pour identifier un module DRM/Runtime.

Si le niveau de sécurité minimum est défini, la version du client (spécifiée dans le jeton de la machine) doit être supérieure ou égale à la valeur spécifiée.

Si une liste de versions exclues est spécifiée et que la version du client correspond à l’un des identifiants de version de la liste, le client ne sera pas autorisé à utiliser un droit contenant cette instance ModuleRequirements. Pour qu’un module corresponde aux informations de version, tous les paramètres spécifiés dans les informations de version, à l’exception de la version de publication, doivent correspondre exactement aux valeurs des modules. La version de publication correspond si la valeur du module client est inférieure ou égale à la valeur dans les informations de version.

Dans le cas où une violation est signalée avec un client DRM ou une version d’exécution spécifique, le propriétaire du contenu et le répartiteur de contenu (qui exécute le serveur de licences) peuvent configurer le serveur pour refuser d’émettre des licences pendant une période pendant laquelle l’Adobe n’a pas de correctif disponible. Vous pouvez le configurer via l’option `HandlerConfiguration` comme décrit ci-dessus ou en apportant des modifications à toutes les stratégies. Dans ce dernier cas, vous pouvez gérer une liste de mise à jour de stratégie et l’utiliser pour vérifier si une stratégie a été mise à jour ou révoquée.

Si vous avez besoin d’une version plus récente de Adobe® Flash® Lecteur/Adobe® AIR® Runtime ou de la bibliothèque Adobe de protection du contenu (module DRM), mettez à jour vos stratégies comme illustré dans la section [Mise à jour d’une stratégie à l’aide de l’API Java](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md) et créez une liste de mise à jour de stratégie ou définissez des restrictions dans `HandlerConfiguration` en appelant `HandlerConfiguration.setRuntimeModuleRequirements()` ou `HandlerConfiguration.setDRMModuleRequirements()`. Lorsqu’un utilisateur demande une nouvelle licence pour laquelle ces listes bloquées sont activées, les nouvelles versions d’exécution et bibliothèques doivent être installées avant qu’une licence ne puisse être émise. Pour obtenir un exemple sur la liste bloquée des versions DRM et d’exécution, reportez-vous à l’exemple de code dans [Mise à jour d’une stratégie à l’aide de l’API Java](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md).
