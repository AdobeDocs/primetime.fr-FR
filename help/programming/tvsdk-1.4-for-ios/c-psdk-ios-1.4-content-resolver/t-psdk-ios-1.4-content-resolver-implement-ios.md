---
description: Vous pouvez mettre en oeuvre vos résolveurs en fonction des résolveurs par défaut.
seo-description: Vous pouvez mettre en oeuvre vos résolveurs en fonction des résolveurs par défaut.
seo-title: Mise en oeuvre d’un outil personnalisé de résolution de contenu/d’opportunités
title: Mise en oeuvre d’un outil personnalisé de résolution de contenu/d’opportunités
uuid: bfc14318-ca4b-46cc-8128-e3743af06d9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Implémenter un outil personnalisé de résolution de contenu/opportunité{#implement-a-custom-opportunity-content-resolver}

Vous pouvez mettre en oeuvre vos résolveurs en fonction des résolveurs par défaut.

<!--<a id="fig_CC41E2A66BDB4115821F33737B46A09B"></a>-->

![](assets/ios_psdk_content_resolver.png)

1. Développez un outil de résolution d&#39;annonces personnalisé en étendant la classe abstraite `PTContentResolver`.

   `PTContentResolver` est une interface qui doit être implémentée par une classe de résolveur de contenu. Une classe abstraite portant le même nom est également disponible et traite automatiquement la configuration (en obtenant le délégué).

   >[!TIP]
   >
   >`PTContentResolver` est exposée à travers la  `PTDefaultMediaPlayerClientFactory` classe. Les clients peuvent enregistrer un nouveau résolveur de contenu en étendant la classe abstraite `PTContentResolver`. Par défaut, et à moins d&#39;être spécifiquement supprimé, un `PTDefaultAdContentResolver` est enregistré dans le `PTDefaultMediaPlayerClientFactory`.

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

1. Implémentez `shouldResolveOpportunity` et renvoyez `YES` s&#39;il doit gérer le `PTPlacementOpportunity` reçu.
1. Implémentez `resolvePlacementOpportunity`, qui début le chargement du contenu ou des publicités alternatif.
1. Une fois les publicités chargées, préparez un `PTTimeline` contenant les informations sur le contenu à insérer.

       Voici quelques informations utiles sur les calendriers :
   
   * Il peut y avoir plusieurs `PTAdBreak`s de types pre-roll, mid-roll et post-roll.

      * Un `PTAdBreak` comporte les éléments suivants :

         * `CMTimeRange` avec l&#39;heure et la durée de début de la coupure.

            Il s’agit de la propriété range de `PTAdBreak`.

         * `NSArray` de  `PTAd`s.

            Il s’agit de la propriété ads de `PTAdBreak`.
   * Un `PTAd` représente la publicité et chaque `PTAd` possède les éléments suivants :

      * `PTAdHLSAsset` est défini comme la Principale propriété de l&#39;actif de la publicité.
      * Vous pouvez créer plusieurs instances `PTAdAsset` en tant que publicités ou bannières cliquables.

   Par exemple :

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

1. Appelez `didFinishResolvingPlacementOpportunity`, qui fournit `PTTimeline`.
1. Enregistrez votre outil de résolution de contenu/publicités personnalisé dans la fabrique de lecteur de médias par défaut en appelant `registerContentResolver`.

   ```
   //Remove default content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearContentResolvers]; 
   
   //Create an instance of your content/ad resolver (id <PTContentResolver>) 
   CustomContentResolver *contentResolver = [[CustomContentResolver alloc] init]; 
   
   //Set custom content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] registerContentResolver:[contentResolver autorelease]];
   ```

1. Si vous avez mis en oeuvre un résolveur d’opportunités personnalisé, enregistrez-le dans la fabrique de lecteur de médias par défaut.

   >[!TIP]
   >
   >Vous n&#39;avez pas besoin d&#39;enregistrer un résolveur d&#39;opportunités personnalisé pour enregistrer un résolveur de contenu/publicités personnalisé.

   ```
   //Remove default opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearOpportunityResolvers]; 
   
   //Create an instance of your opportunity resolver (id <PTOpportunityResolver>) 
   CustomOpportunityResolver *opportunityResolver = [[CustomOpportunityResolver alloc] init]; 
   
   //Set custom opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory]  
              registerOpportunityResolver:[opportunityResolver autorelease]];
   ```

Lorsque le lecteur charge le contenu et qu’il est déterminé qu’il est de type VOD ou LIVE, l’un des événements suivants se produit : >
* Si le contenu est VOD, le programme de résolution de contenu personnalisé est utilisé pour obtenir la chronologie publicitaire de la vidéo entière.
* Si le contenu est LIVE, le programme de résolution de contenu personnalisé est appelé chaque fois qu’une opportunité de placement (indice) est détectée dans le contenu.
