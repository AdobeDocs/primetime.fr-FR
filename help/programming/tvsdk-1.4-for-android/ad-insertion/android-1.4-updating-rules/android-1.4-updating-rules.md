---
description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation des URL sources pour les créatifs publicitaires.
keywords: règles de sélection créative;AdobeTVSDKConfig;priorités créatives;règles de transformation
title: Mise à jour des règles de sélection créative
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Présentation {#updating-ad-creative-selection-rules-overview}

Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation des URL sources pour les créatifs publicitaires.

Lorsque votre lecteur vidéo envoie une requête à un serveur de publicités, la réponse VAST/VMAP comprend généralement plusieurs créations publicitaires ( `MediaFile` ), chacun fournissant une URL vers une version de conteneur-codec différente. Dans certains cas, les créatifs publicitaires dans la réponse VAST/VMAP fournissent chacun un débit différent pour la publicité. Si vous souhaitez définir vos propres priorités et règles de transformation pour ces créatifs publicitaires, vous pouvez le faire dans la variable [!DNL AdobeTVSDKConfig.json] fichier de configuration.

>[!IMPORTANT]
>
>* Ne modifiez pas le nom du fichier de configuration TVSDK. Le nom doit rester [!DNL AdobeTVSDKConfig.json].
>* Ce fichier doit être placé dans la variable [!DNL assets/] du projet.
>

Vous pouvez spécifier deux types de règles dans [!DNL AdobeTVSDKConfig.json]: *Priorité* règles et *Normaliser* règles.

## Désactivation du pré-défilement {#disabling-preroll}

Pour désactiver le preroll, vous devez modifier les générateurs d’opportunités par défaut afin de ne pas effectuer l’appel preroll. Par défaut, TVSDK utilise les générateurs d’opportunités suivants :

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

Pour désactiver le preroll sur les diffusions en direct, cela doit changer afin d’inclure uniquement SpliceOutOpportunityGenerator :

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
