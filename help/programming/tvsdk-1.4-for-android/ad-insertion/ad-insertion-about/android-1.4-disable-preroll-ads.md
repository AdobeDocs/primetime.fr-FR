---
title: Désactiver les publicités preroll
description: Désactiver les publicités preroll
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 0%

---

# Désactiver les publicités preroll{#disable-pre-roll-ads}

Pour désactiver le preroll, modifiez les générateurs d’opportunités par défaut afin de ne pas effectuer l’appel preroll. Les générateurs d’opportunités par défaut sont les suivants :

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

Pour désactiver le preroll sur les diffusions en direct, modifiez la règle ci-dessus pour inclure uniquement SpliceOutOpportunityGenerator :

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
