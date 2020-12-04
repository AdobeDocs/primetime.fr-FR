---
description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection publicitaire créative sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection publicitaire créative sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.
seo-title: Mise à jour des règles de sélection publicitaire
title: Mise à jour des règles de sélection publicitaire
uuid: 84cc13d1-21a3-456b-95c8-200bfec7b453
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Aperçu {#updating-ad-creative-selection-rules-overview}

Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection publicitaire créative sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.

Lorsque votre lecteur vidéo envoie une requête à un serveur d’annonces, la réponse VAST/VMAP comprend généralement plusieurs éléments créatifs publicitaires ( `MediaFile` éléments), chacun d’eux fournissant une URL vers une version de conteneur-codec différente. Dans certains cas, les créatifs publicitaires dans la réponse VAST/VMAP fournissent chacun un débit différent pour la publicité. Si vous souhaitez définir vos propres règles de priorité et de transformation pour ces créatifs publicitaires, vous pouvez le faire dans le fichier de configuration [!DNL AdobeTVSDKConfig.json].

>[!IMPORTANT]
>
>* Ne modifiez pas le nom du fichier de configuration TVSDK. Le nom doit rester [!DNL AdobeTVSDKConfig.json].
>* Ce fichier doit être placé dans le dossier [!DNL assets/] de votre projet.

>



Vous pouvez spécifier deux types de règles dans [!DNL AdobeTVSDKConfig.json] : *Règles de priorité* et *Normaliser* règles.

## Désactivation de la fonction de pré-roulement {#disabling-preroll}

Pour désactiver le pré-roulement, vous devez modifier les générateurs d&#39;opportunités par défaut pour ne pas effectuer l&#39;appel pré-roulement. Par défaut, TVSDK utilise les générateurs d’opportunités suivants :

```
/** 
 * @inheritDoc 
 */ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
    var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
    result.push(new AdSignalingModeOpportunityGenerator()); 
    result.push(new SpliceOutOpportunityGenerator()); 
    return result; 
} 
```

Pour désactiver le prédéploiement sur les flux en direct, cette modification doit être modifiée afin d’inclure uniquement SpliceOutOpportunityGenerator :

```
/** 
 * @inheritDoc 
 */ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
    var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
    if (preroll_enabled == true) { 
        result.push(new AdSignalingModeOpportunityGenerator()); 
    } 
    result.push(new SpliceOutOpportunityGenerator()); 
    return result; 
}
```

