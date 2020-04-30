---
seo-title: Révocation des informations d’identification du client et de l’exécution DRM
title: Révocation des informations d’identification du client et de l’exécution DRM
uuid: 8e36536a-8eed-4d27-8a5f-8d3219817e57
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Révocation des informations d’identification du client et de l’exécution DRM {#revoking-drm-client-and-runtime-credentials}

Les versions DRM/Runtime sont identifiées par le niveau de sécurité, le numéro de version et d&#39;autres attributs, y compris le système d&#39;exploitation et l&#39;exécution. Pour limiter les versions DRM/Runtime autorisées, définissez les restrictions de module dans une stratégie DRM ou dans une `HandlerConfiguration`stratégie. Les restrictions de module peuvent inclure un niveau de sécurité minimum et la liste des versions de module qui ne sont pas autorisées à recevoir une licence.

Pour plus d&#39;informations sur les attributs utilisés pour identifier un module DRM/Runtime, consultez [Liste noire des clients DRM interdits d&#39;accès au contenu](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blacklist-drm-clients.md) protégé.

Si le niveau de sécurité minimum est défini, la version sur le client (spécifiée dans le jeton de l&#39;ordinateur) doit être supérieure ou égale à la valeur spécifiée.

Si une liste de versions exclues est spécifiée et que la version du client correspond à l’un des identifiants de version de la liste, le client n’est pas autorisé à utiliser un droit contenant cette instance ModuleRequirements. Pour qu&#39;un module corresponde aux informations de version, tous les paramètres spécifiés dans les informations de version, à l&#39;exception de la version de publication, doivent correspondre exactement aux valeurs des modules. La version de publication correspond si la valeur du module client est inférieure ou égale à la valeur des informations de version.

Dans le événement où une violation est signalée avec un client DRM ou une version d’exécution particulier, le propriétaire du contenu et le diffuseur de contenu (qui exécute le serveur de licences) peuvent configurer le serveur pour qu’il refuse d’émettre des licences pendant une période pendant laquelle Adobe n’a pas de correctif disponible. Ceci peut être configuré via la `HandlerConfiguration` méthode décrite ci-dessus, ou en apportant des modifications à toutes les stratégies DRM. Dans ce dernier cas, vous pouvez conserver une liste de mise à jour de stratégie DRM et l&#39;utiliser pour vérifier si une stratégie DRM a été mise à jour ou révoquée.

Si vous avez besoin d’une version plus récente d’Adobe Flash Player/Adobe AIR Runtime ou de la bibliothèque Adobe Content Protection (module DRM), vous devez mettre à jour vos stratégies DRM.

Voir [Mise à jour d’une stratégie à l’aide de l’API](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md)Java.

Ensuite, vous devez créer une Liste de mise à jour de stratégie DRM ou définir des restrictions dans `HandlerConfiguration` en appelant `HandlerConfiguration.setRuntimeModuleRequirements()` ou `HandlerConfiguration.setDRMModuleRequirements()`. Lorsqu’un utilisateur demande une nouvelle licence pour laquelle les listes noires spécifiées sont activées, vous devez installer les derniers runtimes et bibliothèques avant de pouvoir émettre une licence.

Consultez l’exemple de code dans [Mise à jour d’une stratégie à l’aide de l’API Java Pour obtenir un exemple sur la mise en liste noire des versions](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) DRM et d’exécution, reportez-vous à la section Mise à jour d’une stratégie à l’aide de l’API Java.
