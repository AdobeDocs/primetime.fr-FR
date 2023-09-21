---
description: Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.
title: Mise en oeuvre d’un outil de résolution de contenu personnalisé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Mise en oeuvre d’un outil de résolution de contenu personnalisé {#implement-a-custom-content-resolver}

Vous pouvez mettre en oeuvre vos propres résolveurs de contenu en fonction des résolveurs par défaut.

Lorsque TVSDK génère une nouvelle opportunité, il effectue une itération via les résolveurs de contenu enregistrés à la recherche d’un résolveur capable de résoudre cette opportunité. La première qui renvoie `true` est sélectionné pour résoudre l’opportunité. Si aucun résolveur de contenu n’est capable, cette opportunité est ignorée. Comme le processus de résolution de contenu est généralement asynchrone, le résolveur de contenu est chargé d’informer TVSDK une fois le processus terminé.

1. Mettez en oeuvre votre propre personnalisation `ContentFactory`, en étendant la variable `ContentFactory` interface et remplacement `retrieveResolvers`.

   Par exemple :

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

1. Enregistrez le `ContentFactory` à la fonction `MediaPlayer`.

   Par exemple :

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

1. Transmettre `AdvertisingMetadata` vers TVSDK comme suit :
   1. Créez un `AdvertisingMetadata` .
   1. Enregistrez le `AdvertisingMetadata` vers `MediaPlayerItemConfig`.

      ```java
      AdvertisingMetadata advertisingMetadata = new AdvertisingMetadata(); 
      
      advertisingMetadata.setDelayAdLoading(true); 
      ... 
      
      mediaPlayerItemConfig.setAdvertisingMetadata(advertisingMetadata); 
      ```

1. Créez une classe de résolveur d’annonces personnalisée qui étend la variable `ContentResolver` classe .
   1. Dans le programme de résolution de publicités personnalisé, remplacez `doConfigure`, `doCanResolve`, `doResolve`, `doCleanup`:

      ```java
      void doConfigure(MediaPlayerItem item); 
      boolean doCanResolve(Opportunity opportunity); 
      void doResolve(Opportunity opportunity); 
      void doCleanup();
      ```

      Vous obtenez votre `advertisingMetadata` de l’élément transmis `doConfigure`:

      ```java
      MediaPlayerItemConfig itemConfig = item.getConfig(); 
      
      AdvertisingMetadata advertisingMetadata =  
        mediaPlayerItemConfig.getAdvertisingMetadata(); 
      ```

   1. Pour chaque opportunité d’emplacement, créez une `List<TimelineOperation>`.

      Cet exemple `TimelineOperation` fournit une structure pour `AdBreakPlacement`:

      ```java
      AdBreakPlacement( 
          new AdBreak( ads,    // Vector<Ad> 
                       tracker // Content Tracker 
          ), 
          placementInformation // Retrieved from Opportunity 
      ); 
      ```

   1. Une fois les publicités résolues, appelez l’une des fonctions suivantes :

      * Si la résolution de publicité réussit, appelez `process(List<TimelineOperation> proposals)` et `notifyCompleted(Opportunity opportunity)` sur le `ContentResolverClient`

        ```java
        _client.process(timelineOperations); 
        _client.notifyCompleted(opportunity); 
        ```

      * Si la résolution de la publicité échoue, appelez `notifyResolveError` sur le `ContentResolverClient`

        ```java
        _client.notifyFailed(Opportunity opportunity, PSDKErrorCode error);
        ```

        Par exemple :

        ```java
        _client.notifyFailed(opportunity, UNSUPPORTED_OPERATION);
        ```

<!--<a id="example_463B718749504A978F0B887786844C39"></a>-->

Cet exemple de résolveur de publicités personnalisées résout une opportunité et diffuse une publicité simple :

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
