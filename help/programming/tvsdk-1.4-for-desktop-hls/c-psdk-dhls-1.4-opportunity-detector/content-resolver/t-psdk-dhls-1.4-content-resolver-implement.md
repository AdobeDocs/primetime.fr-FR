---
description: Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.
seo-description: Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.
seo-title: Mise en oeuvre d’un outil de résolution de contenu personnalisé
title: Mise en oeuvre d’un outil de résolution de contenu personnalisé
uuid: 1714fcd9-45e0-48be-97f3-f702265128a4
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 2%

---


# Mise en oeuvre d’un résolveur de contenu personnalisé{#implement-a-custom-content-resolver}

Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.

Lorsque TVSDK détecte une nouvelle opportunité, il effectue une itération via les résolveurs de contenu enregistrés à la recherche d&#39;une opportunité capable de résoudre cette opportunité à l&#39;aide de la méthode `canResolve`. Le premier qui renvoie true est sélectionné pour résoudre l&#39;opportunité. Si aucun outil de résolution de contenu n’est capable, cette opportunité est ignorée. Le processus de résolution du contenu étant généralement asynchrone, le résolveur de contenu est responsable de l’avertissement de TVSDK une fois le processus terminé.

* Le résolveur de contenu appelle `client.place` pour spécifier l’opération de chronologie à exécuter par TVSDK (généralement un placement de coupures publicitaires).
* Le résolveur de contenu appelle `client.notifyCompleted` si le processus de résolution a réussi ou `client.notifyFailed` si le processus a échoué.

1. Créez un résolveur d&#39;opportunités personnalisé.

   ```
   public class CustomResolver extends ContentResolver { 
   
       /** 
        * Default constructor. 
        */ 
       public function CustomResolver() { 
       } 
   
       override protected function doConfigure(item:MediaPlayerItem):void { 
           // here you can read any media stream characteristics which 
           // might help configure your content resolver like 
           // - the media player item configuration through the item.config 
           // - the media resource metadata through item.resource.metadata 
       } 
   
       /** 
        * @inheritDoc 
        */ 
       override protected function doCanResolve(opportunity:Opportunity):Boolean { 
           // check if the opportunity can be resolved by this resolver 
           // if yes return true, otherwise return false 
   
           return true; 
       } 
   
       /** 
        * @inheritDoc 
        */ 
       override protected function doResolve(opportunity:Opportunity):void { 
           // start the resolving process 
           // communicate with your custom ad server 
   
           // in this example we assume that: 
           // - if successful, onResolveCompleted method will be invoked 
           // - if failed, onResolveFailed method will be invoked 
       } 
   
       private function onResolveCompleted(response:*):void { 
           try { 
               var proposals:Vector.<TimelineOperation> = new Vector.<TimelineOperation>(); 
   
               // extract the timeline ad placement from the response 
               // and add them to the proposal vector 
               // - extract the ad break 
               // - calculate the placement ( can reuse the opportunity.placement ) 
               // var timelineOperation:AdBreakPlacement = new AdBreakPlacement(placement, adBreak); 
               // proposals.push(timelineOperation); 
   
               client.process(proposals); 
               client.notifyCompleted(_opportunity); 
           } catch (error:Error) { 
               onResolveFailed(error); 
           } 
       } 
   
       private function onResolveFailed(error:Error):void { 
   
           var errorMetadata:Metadata = new Metadata(); 
           MetadataUtils.serializeError(error, errorMetadata); 
   
           var mediaError:MediaError = new MediaError(NotificationCode.CONTENT_RESOLVING_ERROR, errorMetadata); 
           client.notifyFailed(_opportunity, mediaError); 
       } 
   
       ... 
   }
   ```

1. Créez la fabrique de contenu personnalisée qui utilise le résolveur de contenu personnalisé.

   Par exemple :

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
           ... 
   
           /** 
            * @inheritDoc 
            */ 
           override protected function  
             doRetrieveResolvers(item:MediaPlayerItem):Vector.<ContentResolver> { 
               var result:Vector.<ContentResolver> = new Vector.<ContentResolver>(); 
   
               var resource:MediaResource = item.resource; 
   
               if (resource.metadata != null) { 
                   if (resource.metadata.containsKey(DefaultMetadataKeys.AUDITUDE_METADATA_KEY)) { 
                       result.push(new AuditudeAdResolver()); 
                   } else if (resource.metadata.containsKey("custom-opportunity-detector")) { 
                       result.push(new CustomResolver()); 
                   } 
               } 
               return result; 
           } 
   }
   ```

1. Enregistrez la fabrique de contenu personnalisée pour que le flux média soit lu.

   Par exemple :

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   var advertisingMetadata:AdvertisingMetadata = new AdvertisingMetadata(); 
   // set any parameter you need for custom ad resolver 
   // advertisingMetadata.setValue("customparam", "customvalue"); 
   
   var metadata:Metadata = new Metadata(); 
   metadata.setMetadata("custom-opportunity-detector", advertisingMetadata); 
   var mediaResource:MediaResource = MediaResource.createFromUrl(url, metadata);
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

