---
description: L’insertion d’une publicité résout les publicités pour la vidéo à la demande (VOD), pour la diffusion en direct et pour la diffusion linéaire avec le suivi des publicités et la lecture des publicités. TVSDK envoie les requêtes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et les place dans le contenu par phases.
seo-description: L’insertion d’une publicité résout les publicités pour la vidéo à la demande (VOD), pour la diffusion en direct et pour la diffusion linéaire avec le suivi des publicités et la lecture des publicités. TVSDK envoie les requêtes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et les place dans le contenu par phases.
seo-title: Insertion de publicités
title: Insertion de publicités
uuid: 25c79822-a861-427b-b6a8-24714b21aae4
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Présentation {#inserting-ads-overview}

L’insertion d’une publicité résout les publicités pour la vidéo à la demande (VOD), pour la diffusion en direct et pour la diffusion linéaire avec le suivi des publicités et la lecture des publicités. TVSDK envoie les requêtes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et les place dans le contenu par phases.

Une *`ad break`* publicité contient une ou plusieurs publicités lues en séquence. TVSDK insère des publicités dans le contenu principal en tant que membres d’une ou de plusieurs coupures publicitaires.

## Désactivation des publicités preroll {#disable-preroll-ads}

Pour désactiver le pré-roulement, modifiez les générateurs d’opportunités par défaut afin de ne pas effectuer l’appel pré-roll. Les générateurs d’opportunités par défaut sont les suivants :

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

Pour désactiver le pré-déploiement sur les flux en direct, modifiez ce qui précède afin d’inclure uniquement SpliceOutOpportunityGenerator :

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
