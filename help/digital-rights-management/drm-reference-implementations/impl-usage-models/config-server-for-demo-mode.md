---
title: Configuration du mode de démonstration du modèle d’utilisation
description: Configuration du mode de démonstration du modèle d’utilisation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Configuration du mode de démonstration du modèle d’utilisation{#configure-usage-model-demo-mode}

Avant que le serveur d’implémentation de référence puisse émettre des licences pour la démonstration du modèle d’utilisation, vous devez configurer le serveur pour spécifier la manière dont les licences sont générées pour chacun des quatre modèles d’utilisation. Cela signifie que vous devez spécifier une stratégie DRM pour chaque modèle d’utilisation. La mise en oeuvre de référence comprend les exemples de stratégies DRM suivants dans la [!DNL Reference Implementation/Server/Reference Implementation Server/resources/] directory:

* `dto-policy.pol` - (Téléchargement personnel)
* `vod-policy.pol` - (location/vidéo à la demande)
* `sub-policy.pol` - (Abonnement)
* `ad-policy.pol` - (financement publicitaire)

>[!NOTE]
>
>Vous pouvez remplacer ces exemples de stratégies par vos propres stratégies DRM.

1. Définissez ces propriétés dans [!DNL flashaccess-refimpl.properties] pour spécifier la stratégie DRM que vous prévoyez d’appliquer à chaque modèle d’utilisation :

   ```
   # DRM Policy file name for Download To Own usage 
   RefImpl.UsageModelDemo.Policy.DTO=dto-policy.pol 
   # DRM Policy file name for Rental usage 
   RefImpl.UsageModelDemo.Policy.VOD=vod-policy.pol 
   # DRM Policy file name for Subscription usage 
   RefImpl.UsageModelDemo.Policy.Subscribe=sub-policy.pol 
   # DRM Policy file name for Ad Supported (free) usage 
   RefImpl.UsageModelDemo.Policy.Free=ad-policy.pol
   ```

1. Copiez vos exemples de fichiers de stratégie dans le répertoire que vous spécifiez dans le `config.resourcesDirectory` dans [!DNL flashaccess-refimpl.properties].
