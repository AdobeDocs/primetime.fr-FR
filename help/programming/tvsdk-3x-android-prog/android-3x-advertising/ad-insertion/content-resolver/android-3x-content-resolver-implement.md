---
description: Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.
seo-description: Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.
seo-title: Mise en oeuvre d’un outil de résolution de contenu personnalisé
title: Mise en oeuvre d’un outil de résolution de contenu personnalisé
uuid: 5f63cc1e-3f4b-460c-9151-2b9d364800e2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 2%

---


# Mise en oeuvre d’un outil de résolution de contenu personnalisé {#implement-a-custom-content-resolver}

Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.

Lorsque TVSDK génère une nouvelle opportunité, il effectue une itération à travers les résolveurs de contenu enregistrés à la recherche d&#39;une opportunité capable de résoudre cette opportunité. Le premier qui renvoie `true` est sélectionné pour résoudre l&#39;opportunité. Si aucun outil de résolution de contenu n’est capable, cette opportunité est ignorée. Le processus de résolution du contenu étant généralement asynchrone, le résolveur de contenu est responsable de l’avertissement de TVSDK une fois le processus terminé.

1. Mettez en oeuvre votre propre `ContentFactory` personnalisé en étendant l&#39;interface `ContentFactory` et en remplaçant `retrieveResolvers`.

   Par exemple :

   ```java
   class MyContentFactory extends ContentFactory { 
       @Override 
       public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { 
           List<ContentResolver> resolvers = new ArrayList<ContentResolver>(); 
           MediaPlayerItemConfig itemConfig = item.getConfig(); 
           if(itemConfig) { 
               CustomRangeMetadata customRanges = itemConfig.getCustomRangeMetadata(); 
               if (customRanges) { 
                   List<ReplaceTimeRange> timeRanges = customRanges.getTimeRangeList(); 
   
                   if (timeRanges && timeRanges.size() > 0) 
                   { 
                   // CustomRangeResolver is only activated by the presence of CustomRanges in configuration 
                   resolvers.add(new CustomRangeResolver()); 
                   } 
               } 
               AdvertisingMetadata metadata = itemConfig.getAdvertisingMetadata(); 
               if (metadata) { 
                   if (metadata instanceOf AuditudeSettings)  
                       resolvers.add(new AuditudeResolver(getContext());    
                   } 
               } 
           // add your custom resolver if any 
           resolvers.add(MyOpportunityGenerator(item)); 
           return resolvers; 
       } 
       ... 
   } 
   ```

1. Enregistrez le `ContentFactory` dans le `MediaPlayer`.

   Par exemple :

   ```java
   //Register the custom content factory with the media player 
   MediaPlayerItemConfig config = new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new MyContentFactory()); 
   
   //Pass this config while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config); 
   
   // OR use MediaPlayerItemLoader to pre-load a resource 
   id = 23; 
   itemLoader.load(resource, id, config);
   ```

1. Transmettez un objet `AdvertisingMetadata` à TVSDK comme suit :
   1. Créez un objet `AdvertisingMetadata`.
   1. Enregistrez l&#39;objet `AdvertisingMetadata` dans `MediaPlayerItemConfig`.

      ```java
      AdvertisingMetadata advertisingMetadata = new AdvertisingMetadata(); 
      
      advertisingMetadata.setDelayAdLoading(true); 
      ... 
      
      mediaPlayerItemConfig.setAdvertisingMetadata(advertisingMetadata); 
      ```

1. Créez une classe de résolution d&#39;annonces personnalisée qui étend la classe `ContentResolver`.
   1. Dans le résolveur d’annonces personnalisé, remplacez `doConfigure`, `doCanResolve`, `doResolve`, `doCleanup` :

      ```java
      void doConfigure(MediaPlayerItem item); 
      boolean doCanResolve(Opportunity opportunity); 
      void doResolve(Opportunity opportunity); 
      void doCleanup();
      ```

      Vous obtenez votre `advertisingMetadata` de l&#39;élément transmis dans `doConfigure` :

      ```java
      MediaPlayerItemConfig itemConfig = item.getConfig(); 
      
      AdvertisingMetadata advertisingMetadata =  
        mediaPlayerItemConfig.getAdvertisingMetadata(); 
      ```

   1. Pour chaque opportunité de placement, créez un `List<TimelineOperation>`.

      Cet exemple `TimelineOperation` fournit une structure pour `AdBreakPlacement` :

      ```java
      AdBreakPlacement( 
          new AdBreak( ads,    // Vector<Ad> 
                       tracker // Content Tracker 
          ), 
          placementInformation // Retrieved from Opportunity 
      ); 
      ```

   1. Une fois les publicités résolues, appelez l’une des fonctions suivantes :

      * Si la résolution de la publicité réussit, appelez `process(List<TimelineOperation> proposals)` et `notifyCompleted(Opportunity opportunity)` sur le `ContentResolverClient`

         ```java
         _client.process(timelineOperations); 
         _client.notifyCompleted(opportunity); 
         ```

      * Si la résolution de la publicité échoue, appelez `notifyResolveError` sur la `ContentResolverClient`

         ```java
         _client.notifyFailed(Opportunity opportunity, PSDKErrorCode error);
         ```

         Par exemple :

         ```java
         _client.notifyFailed(opportunity, UNSUPPORTED_OPERATION);
         ```

<!--<a id="example_463B718749504A978F0B887786844C39"></a>-->

Cet exemple de résolveur d&#39;annonces personnalisé résout une opportunité et sert une publicité simple :

```java
public class CustomContentResolver extends ContentResolver { 
    protected void doConfigure(MediaPlayerItem item){} 
 
    protected boolean doCanResolve(Opportunity opportunity) {  
        return true;  
    } 
 
    protected void doResolve(Opportunity opportunity) { 
        _client.process(createAdBreakPlacementsFor(opportunity.getPlacement())); 
        _client.notifyCompleted(opportunity); 
    } 
 
    private List<TimelineOperation> createAdBreakPlacementsFor(Placement placementInformation) { 
        List<Ad> ads = new ArrayList<Ad>(); 
        AdAsset adAsset = new AdAsset("101", 15000, new MediaResource( 
          "https: . . ..m3u8", MediaResource.Type.HLS, null), null, null); 
 
        Ad ad = Ad.linearFromAsset("101", adAsset, null, null, false); 
        ads.add(ad); 
        AdBreak adBreak = new AdBreak(ads, null, AdInsertionType.CLIENT_INSERTED); 
 
        List<TimelineOperation> result = new ArrayList<TimelineOperation>(); 
 
        result.add(new AdBreakPlacement(placementInformation, adBreak)); 
        return result; 
    } 
 
    protected void doCleanup() {} 
} 
```

