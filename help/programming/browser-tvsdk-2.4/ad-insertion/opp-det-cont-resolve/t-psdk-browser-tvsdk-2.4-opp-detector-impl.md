---
description: Vous pouvez mettre en oeuvre votre propre générateur d'opportunités en étendant l'interface OpportunityGenerator.
seo-description: Vous pouvez mettre en oeuvre votre propre générateur d'opportunités en étendant l'interface OpportunityGenerator.
seo-title: Mise en oeuvre d’un générateur d’opportunités personnalisé
title: Mise en oeuvre d’un générateur d’opportunités personnalisé
uuid: b80da2da-32d5-41f7-86ca-936d6f25b015
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise en oeuvre d’un générateur d’opportunités personnalisé{#implement-a-custom-opportunity-generator}

Vous pouvez mettre en oeuvre votre propre générateur d&#39;opportunités en étendant l&#39;interface OpportunityGenerator.

1. Créez le générateur d’opportunités personnalisé.

   Par exemple :

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

   Par exemple :

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

1. Enregistrez la fabrique de contenu personnalisée pour que le flux média soit lu.

   Dans le lecteur UI Framework, vous pouvez spécifier une fabrique de contenu personnalisée comme suit :

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

