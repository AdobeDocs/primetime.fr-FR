---
description: Vous pouvez mettre en oeuvre votre propre générateur d’opportunités en étendant l’interface OpportunityGenerator.
title: Mise en oeuvre d’un générateur d’opportunités personnalisé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Mise en oeuvre d’un générateur d’opportunités personnalisé{#implement-a-custom-opportunity-generator}

Vous pouvez mettre en oeuvre votre propre générateur d’opportunités en étendant l’interface OpportunityGenerator.

1. Créez le générateur d’opportunités personnalisé.

   Par exemple :

   ```js
   /** 
   * Class implementing AdobePSDK.OpportunityGenerator interface 
   */ 
   CustomOpportunityGenerator = function () { 
   }; 
   
   CustomOpportunityGenerator.prototype = { 
       constructor: CustomOpportunityGenerator, 
       configureCallbackFunc: function (item, client, mode, playhead, playbackRange) {  
           // the playhead represents the initial playback position 
           // the playback range represents the initial playback range 
   
           // the item property indicates the current AdobePSDK.MediaPlayerItem associated with this generator 
           // the initial set of timed metadata can be obtain through the item property 
           var timedMetadatas = item.timedMetadata; 
       }, 
       updateCallbackFunc: function (playhead, playbackRange) { 
           // when an opportunity is created by this generator 
           // we need to notify the TVSDK through the client property 
           client.resolve (opportunity); 
       }, 
       … 
   }; 
   ```

1. Créez la fabrique de contenu personnalisée, qui utilise le générateur d’opportunités personnalisé.

   Par exemple :

   ```js
   /** 
     * Class implementing AdobePSDK.ContentFactory interface 
   */ 
   CustomContentFactory = function () { 
   }; 
   
   CustomContentFactory.prototype = { 
          constructor: CustomContentFactory, 
          retrieveOpportunityGeneratorsCallbackFunc: function (item) { 
               var result = []; 
               result.push (new CustomOpportunityGenerator()); 
               return result; 
       }, 
       … 
   }; 
   ```

1. Enregistrez la fabrique de contenu personnalisée pour que le flux multimédia soit lu.

   Dans le lecteur de structure de l’interface utilisateur, vous pouvez spécifier la fabrique de contenu personnalisée comme suit :

   ```js
   var advertisingFactory = new CustomContentFactory(); 
   var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
           mediaPlayerItemConfig: { 
                   advertisingFactory: advertisingFactory 
           }, 
               mediaResource: { 
                   resourceUrl:'Specify Resource Url' 
          } 
     } 
   }); 
   ```
