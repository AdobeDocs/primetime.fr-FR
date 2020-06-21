---
seo-title: Révocation des informations d’identification du client et de l’exécution DRM
title: Révocation des informations d’identification du client et de l’exécution DRM
uuid: 774b8ac7-51bb-42fc-a05d-cfa718e24a81
translation-type: tm+mt
source-git-commit: fbc175f383c850a7286b1e6e89daa027e00b29ef
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# Révocation des informations d’identification du client et de l’exécution DRM{#revoking-drm-client-and-runtime-credentials}

Les versions DRM/Runtime sont identifiées par le niveau de sécurité, le numéro de version et d&#39;autres attributs, y compris le système d&#39;exploitation et l&#39;exécution. Pour limiter les versions DRM/Runtime autorisées, définissez les restrictions de module dans une stratégie ou dans une `HandlerConfiguration`stratégie. Les restrictions de module peuvent inclure un niveau de sécurité minimum et la liste des versions de module qui ne sont pas autorisées à recevoir une licence. Pour plus d&#39;informations sur les attributs utilisés pour identifier un module DRM/Runtime, voir [Liste bloquée des clients DRM interdits d&#39;accès au contenu](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-blocklist-drm-clients.md) protégé.

Si le niveau de sécurité minimum est défini, la version sur le client (spécifiée dans le jeton de l&#39;ordinateur) doit être supérieure ou égale à la valeur spécifiée.

Si une liste de versions exclues est spécifiée et que la version du client correspond à l’un des identifiants de version de la liste, le client n’est pas autorisé à utiliser un droit contenant cette instance ModuleRequirements. Pour qu&#39;un module corresponde aux informations de version, tous les paramètres spécifiés dans les informations de version, à l&#39;exception de la version de publication, doivent correspondre exactement aux valeurs des modules. La version de publication correspond si la valeur du module client est inférieure ou égale à la valeur des informations de version.

Dans le événement où une violation est signalée avec un client DRM ou une version d’exécution particulier, le propriétaire du contenu et le diffuseur de contenu (qui exécute le serveur de licences) peuvent configurer le serveur pour qu’il refuse d’émettre des licences pendant une période où Adobe n’a pas de correctif disponible. Ceci peut être configuré via la `HandlerConfiguration` méthode décrite ci-dessus ou en apportant des modifications à toutes les stratégies. Dans ce dernier cas, vous pouvez conserver une liste de mise à jour de stratégie et l’utiliser pour vérifier si une stratégie a été mise à jour ou révoquée.

Si vous avez besoin d’une version plus récente de l’environnement d’exécution Adobe® Flash® Player/Adobe® AIR® ou de la bibliothèque Adobe Content Protection (module DRM), mettez à jour vos stratégies comme indiqué dans [Mise à jour d’une stratégie à l’aide de l’API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md) Java et créez une Liste de mise à jour de stratégie, ou définissez des restrictions `HandlerConfiguration` en appelant `HandlerConfiguration.setRuntimeModuleRequirements()` ou `HandlerConfiguration.setDRMModuleRequirements()`. Lorsqu’un utilisateur demande une nouvelle licence avec ces listes bloquées activées, les nouveaux runtimes et bibliothèques doivent être installés pour qu’une licence puisse être émise. Pour un exemple sur la liste des blocs répertoriant les versions DRM et d’exécution, voir l’exemple de code dans [Mise à jour d’une stratégie à l’aide de l’API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md)Java.
