---
seo-title: Révocation des informations d’identification du client et du runtime DRM
title: Révocation des informations d’identification du client et du runtime DRM
uuid: 8e36536a-8eed-4d27-8a5f-8d3219817e57
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Révocation des informations d’identification du client et du runtime DRM {#revoking-drm-client-and-runtime-credentials}

Les versions DRM/Runtime sont identifiées par le niveau de sécurité, le numéro de version et d’autres attributs, y compris le système d’exploitation et le runtime. Pour limiter les versions DRM/Runtime autorisées, définissez les restrictions de module dans une stratégie DRM ou dans une `HandlerConfiguration`stratégie. Les restrictions relatives aux modules peuvent inclure un niveau de sécurité minimum et des  de versions de modules qui ne sont pas autorisées à recevoir une licence.

Pour plus d’informations sur les attributs utilisés pour identifier un module DRM/Runtime, voir [Liste noire des clients DRM interdits d’accès au contenu](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blacklist-drm-clients.md) protégé.

Si le niveau de sécurité minimal est défini, la version sur le client (spécifiée dans le jeton de l’ordinateur) doit être supérieure ou égale à la valeur spécifiée.

Si un de versions exclues est spécifié et que la version du client correspond à l’un des identifiants de version du , le client n’est pas autorisé à utiliser un droit contenant cette instance ModuleRequirements. Pour qu’un module corresponde aux informations de version, tous les paramètres spécifiés dans les informations de version, à l’exception de la version de publication, doivent correspondre exactement aux valeurs des modules. La version de publication correspond si la valeur du module client est inférieure ou égale à la valeur des informations de version.

Dans le , une violation est signalée avec un client DRM ou une version d’exécution spécifique, le propriétaire du contenu et le répartiteur de contenu (qui exécute le serveur de licences) peuvent configurer le serveur pour qu’il refuse d’émettre des licences pendant une période pendant laquelle Adobe n’a pas de correctif disponible. Cette configuration peut s’effectuer via la `HandlerConfiguration` procédure décrite ci-dessus ou en apportant des modifications à toutes les stratégies DRM. Dans ce dernier cas, vous pouvez conserver un de mise à jour de stratégie DRM et l’utiliser pour vérifier si une stratégie DRM a été mise à jour ou révoquée.

Si vous avez besoin d’une version plus récente d’Adobe Flash Player/Adobe AIR Runtime ou de la bibliothèque Adobe Content Protection (module DRM), vous devez mettre à jour vos stratégies DRM.

Voir [Mise à jour d’une stratégie à l’aide de l’API](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md)Java.

Vous devez ensuite créer un de mise à jour de stratégie DRM ou définir des restrictions dans `HandlerConfiguration` en appelant `HandlerConfiguration.setRuntimeModuleRequirements()` ou `HandlerConfiguration.setDRMModuleRequirements()`. Lorsqu’un utilisateur demande une nouvelle licence pour laquelle les listes noires spécifiées sont activées, vous devez installer les derniers moteurs d’exécution et bibliothèques avant de pouvoir émettre une licence.

Voir l’exemple de code dans [Mise à jour d’une stratégie à l’aide de l’API Java Pour obtenir un exemple sur la liste noire des versions](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) DRM et d’exécution, reportez-vous à la section Mise à jour d’une stratégie à l’aide de l’API Java.
