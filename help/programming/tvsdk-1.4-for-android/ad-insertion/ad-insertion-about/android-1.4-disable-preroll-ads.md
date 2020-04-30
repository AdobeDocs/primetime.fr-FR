---
description: 'null'
seo-description: 'null'
seo-title: Désactiver les publicités preroll
title: Désactiver les publicités preroll
uuid: 2e307a58-49f2-43d6-908b-97684ad6e3d3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

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

