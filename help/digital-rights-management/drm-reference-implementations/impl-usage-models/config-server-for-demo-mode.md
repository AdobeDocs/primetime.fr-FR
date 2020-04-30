---
description: 'null'
seo-description: 'null'
seo-title: Configuration du mode de démonstration du modèle d’utilisation
title: Configuration du mode de démonstration du modèle d’utilisation
uuid: f818c7fc-e88f-4fa4-926e-08a1337b28d3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuration du mode de démonstration du modèle d’utilisation{#configure-usage-model-demo-mode}

Avant que le serveur d’implémentation de référence puisse émettre des licences pour la démonstration du modèle d’utilisation, vous devez configurer le serveur pour spécifier comment les licences sont générées pour chacun des quatre modèles d’utilisation. Cela signifie que vous devez spécifier une stratégie DRM pour chaque modèle d&#39;utilisation. L’implémentation de référence comprend les exemples de stratégies DRM suivants dans le [!DNL Reference Implementation/Server/Reference Implementation Server/resources/] répertoire :

* `dto-policy.pol` - (Téléchargement par site)
* `vod-policy.pol` - (Location/Vidéo à la demande)
* `sub-policy.pol` - (Abonnement)
* `ad-policy.pol` - (Publicité financée)

>[!NOTE]
>
>Vous pouvez remplacer ces exemples de stratégies par vos propres stratégies DRM.

1. Définissez ces propriétés dans [!DNL flashaccess-refimpl.properties] pour spécifier la stratégie DRM que vous prévoyez d&#39;appliquer à chaque modèle d&#39;utilisation :

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

1. Copiez les exemples de fichiers de stratégie dans le répertoire que vous spécifiez dans la `config.resourcesDirectory` propriété de [!DNL flashaccess-refimpl.properties].
