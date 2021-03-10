---
description: Pour l’insertion de publicités en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
title: Mise en oeuvre d’un retour anticipé de coupures publicitaires
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 2%

---


# Mettre en oeuvre un retour de coupure publicitaire anticipée {#implement-an-early-ad-break-return}

Pour l’insertion de publicités en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.

Par exemple, la durée de la coupure publicitaire dans certains événements sportifs peut ne pas être connue avant les débuts de coupure. TVSDK fournit une durée par défaut, mais si le jeu reprend avant la fin de la pause, la coupure publicitaire doit être quittée. Un autre exemple est un signal d’urgence pendant une coupure publicitaire dans un flux en direct.

1. Abonnez-vous à `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN` et `#EXT-X-CUE`, qui sont les séparations/splices des marqueurs.
Pour plus d’informations sur la manière de diviser/dans les marqueurs publicitaires, voir [Générateurs d’opportunités et résolveurs de contenu](../../ad-insertion/content-resolver/android-3x-content-resolver.md).
1. Utilisez un `ContentFactory` personnalisé.
1. Dans `retrieveGenerators`, utilisez `SpliceInPlacementOpportunityGenerator`.

   Par exemple :

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Pour plus d&#39;informations sur l&#39;utilisation d&#39;un `ContentFactory` personnalisé, voir l&#39;étape 1 dans [Mise en oeuvre d&#39;un générateur d&#39;opportunités personnalisé](../../ad-insertion/content-resolver/android-3x-opp-detector-impl-android.md).

1. Sur la même personnalisée `ContentFactory`, implémentez `retrieveResolvers` et incluez `AuditudeResolver` et `SpliceInCustomResolver`.

   Par exemple :

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
