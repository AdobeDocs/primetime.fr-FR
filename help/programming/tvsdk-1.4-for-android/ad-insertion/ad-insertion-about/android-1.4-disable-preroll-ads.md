---
title: Désactiver les publicités preroll
description: Désactiver les publicités preroll
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 0%

---


# Désactiver les publicités preroll{#disable-pre-roll-ads}

Pour désactiver le pré-roulement, modifiez les générateurs d&#39;opportunités par défaut afin de ne pas effectuer l&#39;appel de pré-roulement. Les générateurs d&#39;opportunités par défaut sont les suivants :

```
@inheritDoc 
*/ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
result.push(new AdSignalingModeOpportunityGenerator()); 
result.push(new SpliceOutOpportunityGenerator()); 
return result; 
}
```

Pour désactiver le prédéploiement sur les flux en direct, modifiez ce qui précède afin d’inclure uniquement SpliceOutOpportunityGenerator :

```
@inheritDoc 
*/ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
if (preroll_enabled == true) { result.push(new AdSignalingModeOpportunityGenerator()); } 
 
result.push(new SpliceOutOpportunityGenerator()); 
return result; 
}
```

