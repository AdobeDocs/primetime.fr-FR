---
description: Vous pouvez mettre en oeuvre vos propres détecteurs d’opportunités.
seo-description: Vous pouvez mettre en oeuvre vos propres détecteurs d’opportunités.
seo-title: Mise en oeuvre d’un détecteur d’opportunités personnalisé
title: Mise en oeuvre d’un détecteur d’opportunités personnalisé
uuid: 18fb431b-4585-4293-92a7-b77ab7f9b7db
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise en oeuvre d’un détecteur d’opportunités personnalisé{#implement-a-custom-opportunity-detector}

Vous pouvez mettre en oeuvre vos propres détecteurs d’opportunités.

* Si votre générateur d’opportunités est basé sur `TimedMetadata` des objets associés au flux de média actuel, il doit étendre le `SpliceOutOpportunityGenerator` ou `TimedMetadataOpportunityGenerator`.

* Si votre générateur d’opportunités est basé sur des données hors bande fournies par un service externe (un CIS, par exemple), il doit étendre le `OpportunityGenerator`.

1. Créez le générateur d’opportunités personnalisé.

       Si votre générateur d&#39;opportunités personnalisé est basé sur les objets &quot;TimedMetadata&quot;, étendez le paramètre &quot;TimedMetadataOpportunityGenerator&quot; et remplacez les méthodes suivantes :
   
   * `doConfigure` - Cette méthode est appelée une fois que l’élément du lecteur multimédia a été créé et permet au générateur d’opportunités de créer un jeu initial d’opportunités, le cas échéant.
   * `doProcess` - Cette méthode est appelée chaque fois qu’une nouvelle méthode `TimedMetadata` est détectée (par exemple, pour les flux en direct/linéaires chaque fois que la liste de lecture/le manifeste est actualisé).

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

1. Enregistrez la fabrique de contenu personnalisée pour que le flux média soit lu.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

