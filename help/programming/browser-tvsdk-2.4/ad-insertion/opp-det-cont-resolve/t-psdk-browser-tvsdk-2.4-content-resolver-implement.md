---
description: Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.
title: Mise en oeuvre d’un outil de résolution de contenu personnalisé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Mise en oeuvre d’un outil de résolution de contenu personnalisé{#implement-a-custom-content-resolver}

Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.

Lorsque Browser TVSDK détecte une nouvelle opportunité, il effectue une itération via les programmes de résolution de contenu enregistrés à la recherche d’une opportunité capable de résoudre cette opportunité à l’aide de la fonction `canResolve` . La première qui renvoie true (vrai) est sélectionnée pour résoudre l’opportunité. Si aucun résolveur de contenu n’est capable, cette opportunité est ignorée. Comme le processus de résolution de contenu est généralement asynchrone, le résolveur de contenu est chargé d’informer le navigateur TVSDK une fois le processus terminé.

Gardez à l’esprit les informations suivantes :

* Les appels du programme de résolution de contenu `client.process` pour spécifier l’opération de chronologie que TVSDK doit exécuter.

  L’opération est généralement un emplacement de coupure publicitaire.

* Les appels du programme de résolution de contenu `client.notifyCompleted` si le processus de résolution a réussi ou `client.notifyFailed` si le processus échoue.

1. Créez un programme de résolution d’opportunités personnalisé.

   ```js
   /** 
     * Class implementing AdobePSDK.ContentResolver interface  
   */ 
   CustomResolver = function () { 
   }; 
   
   CustomResolver.prototype = { 
       constructor: CustomResolver, 
       configureCallbackFunc: function (item, client) { 
       // here you can read any media stream characteristics which 
       // might help configure your content resolver like 
       // - the media player item configuration through the item.config 
       // - the media resource metadata through item.resource.metadata 
      }, 
   
       canResolveCallbackFunc: function (opportunity) { 
       // check if the opportunity can be resolved by this resolver 
       // if yes return true, otherwise return false 
       return true; 
      }, 
   
       resolveCallbackFunc: function (opportunity) {         
       // start the resolving process 
       // communicate with your custom ad server 
   
       // in this example we assume that: 
       // - if successful, onResolveCompleted method will be invoked 
       // - if failed, onResolveFailed method will be invoked 
      }, 
   
       onResolveCompleted: function (response) { 
        try { 
           var proposals = []; 
           // extract the timeline ad placement from the response 
           // and add them to the proposal vector 
           // - extract the ad break 
           // - calculate the placement (can reuse the _opportunity.placement) 
           // var timelineOperation = new AdobePSDK.AdBreakPlacement (adBreak, placement); 
           // proposals.push (timelineOperation); 
   
           client.process (proposals); 
           client.notifyCompleted (_opportunity); 
       } catch (error) { 
           onResolveFailed (error); 
       } 
   }, 
   
       onResolveFailed: function (error) { 
         client.notifyFailed (_opportunity); 
       } 
   
   }; 
   ```

1. Créez la fabrique de contenu personnalisée, qui utilise le résolveur de contenu personnalisé.

   Par exemple :

   ```js
   /** 
     * Class implementing AdobePSDK.ContentFactory interface 
   */ 
   CustomContentFactory = function () { 
   }; 
   
   CustomContentFactory.prototype = { 
       constructor: CustomContentFactory, 
       retrieveResolversCallbackFunc: function (item) { 
           var result = []; 
           var resource = item.resource; 
           if (resource.metadata.containsKey("custom-opportunity-detector")) { 
               result.push (new CustomResolver()); 
           } 
           return result; 
       }, 
       … 
   }; 
   ```

1. Enregistrez la fabrique de contenu personnalisée pour que le flux multimédia soit lu.

   Dans le lecteur de structure de l’interface utilisateur, vous pouvez spécifier la fabrique de contenu personnalisée comme suit :

   ```js
   var advertisingFactory = new CustomContentFactory(); 
   var advertisingMetadata = new AdobePSDK.AdvertisingMetadata(); 
   // set any parameter you need for custom ad resolver 
   // advertisingMetadata.setValue ("customparam", "customvalue"); 
   
   var metadata = new AdobePSDK.Metadata(); 
   metadata.setMetadata ("custom-opportunity-detector", advertisingMetadata); 
   
   var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
       mediaPlayerItemConfig: { 
              advertisingFactory: advertisingFactory 
       }, 
          mediaResource: { 
                  resourceUrl:'Specify Resource Url', 
                  metadata: metadata 
          } 
   } 
   
   }); 
   ```
