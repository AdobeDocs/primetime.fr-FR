---
description: Pour l’insertion d’une publicité en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
seo-description: Pour l’insertion d’une publicité en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
seo-title: Mise en oeuvre d’un retour de coupure publicitaire anticipée
title: Mise en oeuvre d’un retour de coupure publicitaire anticipée
uuid: 0e77414e-86f5-4979-9caa-eaf2f39144a2
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Mise en oeuvre d’un retour de coupure publicitaire anticipée {#implement-an-early-ad-break-return}

Pour l’insertion d’une publicité en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.

Par exemple, la durée de la coupure publicitaire dans certains sportifs peut ne pas être connue avant le  de coupure. TVSDK fournit une durée par défaut, mais si le jeu reprend avant la fin de la pause, la coupure publicitaire doit être quittée. Un autre exemple est un signal d’urgence pendant une coupure publicitaire dans un flux en direct.

1. Abonnez-vous à `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`et `#EXT-X-CUE`, qui sont les séparations/splices dans les marqueurs.
Pour plus d’informations sur la manière de diviser/dans les marqueurs publicitaires, voir [Générateurs d’opportunités et résolveurs](../../ad-insertion/content-resolver/android-3x-content-resolver.md)de contenu.
1. Utilisez une personnalisation `ContentFactory`.
1. Dans `retrieveGenerators`, utilisez le `SpliceInPlacementOpportunityGenerator`.

   Par exemple :

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Pour plus d’informations sur l’utilisation d’une personnalisation `ContentFactory`, voir l’étape 1 dans [Mise en oeuvre d’un créateur](../../ad-insertion/content-resolver/android-3x-opp-detector-impl-android.md)d’opportunités personnalisé.

1. Sur la même personnalisation `ContentFactory`, implémentez `retrieveResolvers` et incluez `AuditudeResolver` et `SpliceInCustomResolver`.

   Par exemple :

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
