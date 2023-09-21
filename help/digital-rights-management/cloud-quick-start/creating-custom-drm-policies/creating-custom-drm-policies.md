---
title: Création de stratégies DRM personnalisées (facultatif)
description: Création de stratégies DRM personnalisées (facultatif)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Création de stratégies DRM personnalisées (facultatif){#create-custom-drm-policies-optional}

Le kit de protection DRM de Primetime Cloud est fourni avec quelques stratégies préconfigurées qui peuvent être utilisées lors du conditionnement. Si vous souhaitez des configurations de stratégie supplémentaires, par exemple un droit de liste autorisé spécifique pour les SWF, le Gestionnaire de stratégies DRM Primetime inclus peut être utilisé pour générer des stratégies personnalisées.

>[!NOTE]
>
>Toutes les stratégies doivent utiliser l’authentification ANONYMOUS (et non le mot de passe du nom d’utilisateur ou personnalisé), que le workflow Auth/Droit personnalisé soit utilisé ou non.

Le Gestionnaire de stratégies comprend la variable [!DNL flashaccesstools.properties] fichier de configuration, qui a été modifié pour afficher uniquement les options de stratégie configurables prises en charge par le service DRM de Primetime Cloud. La définition d’options de stratégie qui ne sont pas prises en charge par le service Primetime Cloud DRM entraînera des erreurs d’acquisition de licence. Pour plus d’informations sur l’utilisation de Primetime DRM Policy Manager, voir : [Mises en oeuvre de référence DRM Primetime : Policy Manager](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager).

Pour créer une stratégie, mettez à jour la variable [!DNL flashaccesstools.properties] le fichier suivant vos besoins, puis utilisez la commande :

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## Création dynamique de stratégies pour l’authentification/le droit personnalisés{#create-policies-dynamically-for-custom-auth-entitlement}

Si vous utilisez l’authentification/les droits personnalisés DRM de Primetime Cloud et souhaitez créer dynamiquement une stratégie DRM pour chaque demande de licence (au lieu d’extraire des stratégies d’un pool pré-généré), Adobe vous recommande d’utiliser directement le SDK Java DRM Primetime. L’utilisation directe du SDK Java est plus rapide que la [!DNL AdobePolicyManager.jar] qui génère automatiquement le fichier de stratégie sur le disque, ce qui entraîne une surcharge d’E/S du disque.

Vous trouverez un exemple de code à l’aide du SDK Java dans la section [!DNL /Primetime DRM PolicyManager/sampleCode/] répertoire, nommé [!DNL CreatePolicy.java] et [!DNL CreatePolicyWithOutputProtection.java]. Les JavaDocs et la documentation du SDK Java sont disponibles à l’adresse [Présentation du SDK DRM Adobe Primetime](../../../digital-rights-management/drm-sdk-overview/overview.md)

Pour créer et exécuter les exemples, copiez les fichiers .java dans le dossier ../libs/ et exécutez :

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```
