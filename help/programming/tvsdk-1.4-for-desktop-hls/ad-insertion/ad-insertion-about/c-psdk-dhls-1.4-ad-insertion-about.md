---
description: L’insertion de publicités résout les publicités pour la diffusion vidéo à la demande (VOD) , pour la diffusion en direct et pour la diffusion en continu linéaire avec suivi des publicités et lecture de publicité. TVSDK envoie les demandes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et place les publicités dans le contenu par phases.
title: Insérer des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---

# Présentation {#inserting-ads-overview}

L’insertion de publicités résout les publicités pour la diffusion vidéo à la demande (VOD) , pour la diffusion en direct et pour la diffusion en continu linéaire avec suivi des publicités et lecture de publicité. TVSDK envoie les demandes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et place les publicités dans le contenu par phases.

Un *`ad break`* contient une ou plusieurs publicités lues en séquence. TVSDK insère des publicités dans le contenu principal en tant que membres d’une ou de plusieurs coupures publicitaires.

## Désactiver les publicités preroll {#disable-preroll-ads}

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
