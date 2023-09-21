---
description: Vous pouvez mettre en oeuvre vos programmes de résolution en fonction des programmes de résolution par défaut.
title: Mise en oeuvre d’un outil de résolution de contenu/opportunité personnalisé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Mise en oeuvre d’un outil de résolution de contenu/opportunité personnalisé {#implement-a-custom-opportunity-content-resolver}

Vous pouvez mettre en oeuvre vos programmes de résolution en fonction des programmes de résolution par défaut.

<!--<a id="fig_CC41E2A66BDB4115821F33737B46A09B"></a>-->

![](assets/ios_psdk_content_resolver.png)

1. Développez un outil de résolution de publicités personnalisé en étendant la variable `PTContentResolver` classe abstraite.

   `PTContentResolver` est une interface qui doit être implémentée par une classe de résolveur de contenu. Une classe abstraite du même nom est également disponible et gère automatiquement la configuration (récupération du délégué).

   >[!TIP]
   >
   >`PTContentResolver` est exposé à l’aide de la fonction `PTDefaultMediaPlayerClientFactory` classe . Les clients peuvent enregistrer un nouveau résolveur de contenu en étendant la variable `PTContentResolver` classe abstraite. Par défaut, et, sauf suppression spécifique, une `PTDefaultAdContentResolver` est enregistré dans la variable `PTDefaultMediaPlayerClientFactory`.

   ```
   @protocol PTContentResolver <NSObject> 
   @required 
   + (BOOL)shouldHandleOpportunity:(PTPlacementOpportunity *)opportunity;  
   //Detector returns YES/NO if it should handle the following placement opportunity 
   - (void)configWithPlayerItem:(PTMediaPlayerItem *)item  
                 delegate:(id<PTContentResolverDelegate> delegate); 
   - (void)process:(PTPlacementOpportunity *)opportunity; 
   - (void)timeout:(PTPlacementOpportunity *)opportunity;  
   //The timeout method gets invoked if the TVSDK decides that the  
   //PTContentResolver is taking too much time to respond. 
   @end 
   
   @interface PTContentResolver : NSObject <PTContentResolver> 
   
   @property (readonly) id<PTContentResolverDelegate> delegate; 
   @property (readonly) PTMediaPlayerItem *playerItem; 
   
   - (BOOL)shouldHandleOpportunity:(PTPlacementOpportunity *)opportunity; 
   - (void)configWithPlayerItem:(PTMediaPlayerItem *)item  
                  delegate:(id<PTContentResolverDelegate>) delegate; 
   - (void)process:(NSArray *)opportunities; 
   - (void)cancel:(NSArray *)opportunities; 
   @end
   ```

1. Mise en oeuvre `shouldResolveOpportunity` et revenir `YES` si elle doit gérer la réception `PTPlacementOpportunity`.
1. Mise en oeuvre `resolvePlacementOpportunity`, qui commence à charger le ou les publicités de remplacement.
1. Une fois les publicités chargées, préparez une `PTTimeline` avec les informations sur le contenu à insérer.

       Voici quelques informations utiles sur les chronologies :
   
   * Il peut exister plusieurs `PTAdBreak`s de types preroll, mid-roll et post-roll.

      * A `PTAdBreak` possède les éléments suivants :

         * A `CMTimeRange` avec l’heure de début et la durée de la coupure.

           Défini comme propriété range de `PTAdBreak`.

         * `NSArray` de `PTAd`s.

           Défini comme propriété ads de `PTAdBreak`.

   * A `PTAd` représente la publicité, et chaque `PTAd` possède les éléments suivants :

      * A `PTAdHLSAsset` défini comme propriété principale de la publicité.
      * Peut-être plusieurs `PTAdAsset` d’instances comme des annonces cliquables ou des bannières publicitaires.

   Par exemple :

   ```
   NSMutableArray *ptBreaks = [[[NSMutableArray alloc] init] autorelease]; 
   
   // Prepare the primary asset of the ad - links to ad m3u8 
   PTAdHLSAsset *ptAdAsset = [[[PTAdHLSAsset alloc] init] autorelease]; 
   ptAdAsset.source = AD_SOURCE_M3U8; 
   ptAdAsset.id = FAKE_NUMBER_ID; 
   ptAdAsset.format = @"video"; 
   
   // Prepare the ad itself. 
   PTAd *ptAd = [[[PTAd alloc] init] autorelease]; 
   ptAd.primaryAsset = ptAdAsset; 
   ptAd.primaryAsset.ad = ptAd; 
   
   // Prepare the break and add the ad created above. 
   PTAdBreak *ptBreak = [[[PTAdBreak alloc] init] autorelease]; 
   ptBreak.relativeRange = CMTimeRangeMake(BREAK_START_TIME, BREAK_DURATION_VALUE); 
   [ptBreak addAd:ptAd]; 
   
   // Add the break to array of breaks. 
   [ptBreaks addObject:adBreak]; 
   
   // Once all breaks have been prepared, they can be set on timeline 
   PTTimeline *_timeline = [[PTTimeline alloc] init]; 
   _timeline.adBreaks = ptBreaks;
   ```

1. Appeler `didFinishResolvingPlacementOpportunity`, qui fournit la variable `PTTimeline`.
1. Enregistrez votre programme de résolution de contenu/publicités personnalisé dans la fabrique de lecteurs multimédia par défaut en appelant `registerContentResolver`.

   ```
   //Remove default content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearContentResolvers]; 
   
   //Create an instance of your content/ad resolver (id <PTContentResolver>) 
   CustomContentResolver *contentResolver = [[CustomContentResolver alloc] init]; 
   
   //Set custom content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] registerContentResolver:[contentResolver autorelease]];
   ```

1. Si vous avez mis en oeuvre un programme de résolution d’opportunités personnalisé, enregistrez-le dans la fabrique de lecteurs multimédia par défaut.

   >[!TIP]
   >
   >Vous n’avez pas besoin d’enregistrer un résolveur d’opportunités personnalisé pour enregistrer un résolveur de contenu/publicités personnalisé.

   ```
   //Remove default opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearOpportunityResolvers]; 
   
   //Create an instance of your opportunity resolver (id <PTOpportunityResolver>) 
   CustomOpportunityResolver *opportunityResolver = [[CustomOpportunityResolver alloc] init]; 
   
   //Set custom opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory]  
              registerOpportunityResolver:[opportunityResolver autorelease]];
   ```

Lorsque le lecteur charge le contenu et qu’il est déterminé qu’il est de type VOD ou LIVE, l’un des événements suivants se produit :

* Si le contenu est VOD, le programme de résolution de contenu personnalisé est utilisé pour obtenir la chronologie publicitaire de la vidéo entière.
* Si le contenu est LIVE, le programme de résolution de contenu personnalisé est appelé chaque fois qu’une opportunité d’emplacement (point de repère) est détectée dans le contenu.
