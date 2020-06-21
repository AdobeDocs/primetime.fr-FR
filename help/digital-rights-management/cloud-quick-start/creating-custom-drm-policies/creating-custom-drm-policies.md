---
seo-title: Création de stratégies DRM personnalisées (facultatif)
title: Création de stratégies DRM personnalisées (facultatif)
uuid: 701b51d9-6dde-4c21-bc5b-09e612582968
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Création de stratégies DRM personnalisées (facultatif){#create-custom-drm-policies-optional}

Le kit de protection DRM de Primetime Cloud est fourni avec quelques stratégies préconfigurées qui peuvent être utilisées lors de l’assemblage. Si d’autres configurations de stratégie sont souhaitées, par exemple un droit d’Liste autorisée SWF spécifique, le Gestionnaire de stratégies DRM Primetime inclus peut être utilisé pour générer des stratégies personnalisées.

>[!NOTE]
>
>Toutes les stratégies doivent utiliser l’authentification ANONYMOUS (et non le mot de passe du nom d’utilisateur ou le mot de passe personnalisé), que le processus d’authentification/droits personnalisés soit ou non utilisé.

Le gestionnaire de stratégies comprend le fichier de [!DNL flashaccesstools.properties] configuration, qui a été modifié pour n’exposer que les options de stratégie configurables prises en charge par le service DRM de Primetime Cloud. La définition d’options de stratégie qui ne sont pas prises en charge par le service DRM de Primetime Cloud entraîne des erreurs d’acquisition de licence. Pour plus d&#39;informations sur l&#39;utilisation de Primetime DRM Policy Manager, consultez : [Implémentations de référence DRM Primetime : Gestionnaire](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager)de stratégies.

Pour créer une nouvelle stratégie, mettez à jour le [!DNL flashaccesstools.properties] fichier suivant vos besoins, puis utilisez la commande :

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## Créer des stratégies dynamiquement pour l’authentification/les droits personnalisés{#create-policies-dynamically-for-custom-auth-entitlement}

Si vous utilisez l’authentification/droits personnalisés DRM de Primetime Cloud et souhaitez créer de manière dynamique une stratégie DRM pour chaque demande de licence (au lieu d’extraire des stratégies d’un pool pré-généré), Adobe vous recommande d’utiliser directement le SDK Java DRM de Primetime. L’utilisation directe du SDK Java est plus rapide que celle de l’ [!DNL AdobePolicyManager.jar] outil, qui génère automatiquement le fichier de stratégie sur le disque, entraînant une surcharge d’E/S du disque.

Vous trouverez un exemple de code à l’aide du SDK Java dans le [!DNL /Primetime DRM PolicyManager/sampleCode/] répertoire, nommé [!DNL CreatePolicy.java] et [!DNL CreatePolicyWithOutputProtection.java]. Vous trouverez des javadocs et la documentation relative au SDK Java dans [An Overview of Adobe Primetime DRM SDK.](../../../digital-rights-management/drm-sdk-overview/overview.md)

Pour créer et exécuter les exemples, copiez les fichiers .java dans le dossier ../libs/ et exécutez :

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```
