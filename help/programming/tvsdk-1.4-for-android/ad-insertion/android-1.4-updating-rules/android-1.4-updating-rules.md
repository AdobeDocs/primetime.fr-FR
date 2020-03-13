---
description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.
seo-title: Mise à jour des règles de sélection des créatifs publicitaires
title: Mise à jour des règles de sélection des créatifs publicitaires
uuid: 84cc13d1-21a3-456b-95c8-200bfec7b453
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Présentation {#updating-ad-creative-selection-rules-overview}

Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.

Lorsque votre lecteur vidéo émet une requête vers un serveur d’annonces, la réponse VAST/VMAP comprend généralement plusieurs éléments créatifs ( `MediaFile` éléments), qui fournissent chacun une URL vers une version de -codec différente. Dans certains cas, les éléments créatifs de la réponse VAST/VMAP fournissent chacun un débit différent pour la publicité. Si vous souhaitez définir vos propres règles de priorité et de transformation pour ces créatifs publicitaires, vous pouvez le faire dans le fichier de [!DNL AdobeTVSDKConfig.json] configuration.

>[!IMPORTANT]
>
>* Ne modifiez pas le nom du fichier de configuration TVSDK. Le nom doit rester [!DNL AdobeTVSDKConfig.json].
>* Ce fichier doit être placé dans le [!DNL assets/] dossier de votre projet.
>



Vous pouvez spécifier deux types de règles dans [!DNL AdobeTVSDKConfig.json]: Règles de *priorité* et de *normalisation* des règles.

## Désactivation du pré-roulement {#disabling-preroll}

Pour désactiver le pré-roulement, vous devez modifier les générateurs d’opportunités par défaut afin de ne pas effectuer l’appel pré-roll. Par défaut, TVSDK utilise les générateurs d’opportunités suivants :

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

Pour désactiver le pré-déploiement sur les flux en direct, cela doit changer pour inclure uniquement SpliceOutOpportunityGenerator :

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

