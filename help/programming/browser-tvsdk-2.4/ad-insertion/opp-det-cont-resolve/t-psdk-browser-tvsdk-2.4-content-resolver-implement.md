---
description: Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.
seo-description: Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.
seo-title: Mise en oeuvre d’un outil de résolution de contenu personnalisé
title: Mise en oeuvre d’un outil de résolution de contenu personnalisé
uuid: cf85dd90-242e-4f9e-9785-158ca0fc9465
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise en oeuvre d’un outil de résolution de contenu personnalisé{#implement-a-custom-content-resolver}

Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.

Lorsque le navigateur TVSDK détecte une nouvelle opportunité, il effectue une itération à travers les résolveurs de contenu enregistrés à la recherche d&#39;une opportunité capable de résoudre cette opportunité en utilisant la `canResolve` méthode. Le premier qui renvoie true est sélectionné pour résoudre l&#39;opportunité. Si aucun outil de résolution de contenu n’est capable, cette opportunité est ignorée. Le processus de résolution du contenu étant généralement asynchrone, le résolveur de contenu est responsable de la notification du SDK du navigateur une fois le processus terminé.

Rappelez-vous des informations suivantes :

* Le résolveur de contenu appelle `client.process` pour spécifier l’opération de chronologie que TVSDK doit exécuter.

   L’opération est généralement un emplacement de coupure publicitaire.

* Le résolveur de contenu appelle `client.notifyCompleted` si le processus de résolution est réussi ou `client.notifyFailed` si le processus échoue.

1. Créez un résolveur d&#39;opportunités personnalisé.

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

1. Créez la fabrique de contenu personnalisée qui utilise le résolveur de contenu personnalisé.

   Par exemple :

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

1. Enregistrez la fabrique de contenu personnalisée pour que le flux média soit lu.

   Dans le lecteur UI Framework, vous pouvez spécifier une fabrique de contenu personnalisée comme suit :

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

