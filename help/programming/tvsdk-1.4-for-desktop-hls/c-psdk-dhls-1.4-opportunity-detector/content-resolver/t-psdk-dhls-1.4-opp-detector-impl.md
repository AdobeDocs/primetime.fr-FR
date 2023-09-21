---
description: Vous pouvez implémenter vos propres détecteurs d’opportunités.
title: Mise en oeuvre d’un détecteur d’opportunités personnalisé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Mise en oeuvre d’un détecteur d’opportunités personnalisé{#implement-a-custom-opportunity-detector}

Vous pouvez implémenter vos propres détecteurs d’opportunités.

* Si votre générateur d’opportunités est basé sur `TimedMetadata` objets associés au flux multimédia actuel, puis qu’il étende la variable `SpliceOutOpportunityGenerator` ou `TimedMetadataOpportunityGenerator`.

* Si votre générateur d’opportunités est basé sur des données hors-bande fournies par un service externe (un CIS, par exemple), il doit étendre la variable `OpportunityGenerator`.

1. Créez le générateur d’opportunités personnalisé.

       Si votre générateur d’opportunités personnalisé est basé sur des objets &quot;TimedMetadata&quot;, étendez le &quot;TimedMetadataOpportunityGenerator&quot; et remplacez ces méthodes :
   
   * `doConfigure` - Cette méthode est appelée une fois que l’élément du lecteur multimédia a été créé et fournit au générateur d’opportunités la possibilité de créer un jeu initial d’opportunités, si nécessaire.
   * `doProcess` - Cette méthode est appelée chaque fois que de nouvelles `TimedMetadata` est détecté (par exemple, pour les flux en direct/linéaires chaque fois que la liste de lecture/le manifeste est actualisé).

   ```
   public class CustomOpportunityGenerator extends TimedMetadataOpportunityGenerator { 
       override protected function doConfigure(playhead:Number, playbackRange:TimeRange):void { 
           // the playhead represents the initial playback position 
           // the playback range represents the initial playback range 
   
           // the item property indicates the current MediaPlayerItem associated with this generator 
           // the initial set of timed metadata can be obtain through the item property 
           var timedMetadataCollection:Vector.<TimedMetadata> = item.timedMetadata; 
       } 
   
       override protected function doProcess(timedMetadata:TimedMetadata):void { 
           ... 
   
           // when an opportunity is created by this generator 
           // we need to notify the TVSDK through the client property 
           client.resolve(opportunity); 
       }  
       ... 
   }
   ```

1. Créez la fabrique de contenu personnalisée, qui utilise le générateur d’opportunités personnalisé.

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
       ... 
   
       /** 
       * @inheritDoc 
       */ 
       override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
           var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
           result.push(new CustomOpportunityGenerator()); 
   
           return result; 
       } 
   }
   ```

1. Enregistrez la fabrique de contenu personnalisée pour que le flux multimédia soit lu.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
