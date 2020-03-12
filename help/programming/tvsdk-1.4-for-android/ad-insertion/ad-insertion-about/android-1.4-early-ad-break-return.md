---
description: Pour l’insertion d’une publicité en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
seo-description: Pour l’insertion d’une publicité en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
seo-title: Mise en oeuvre d’un retour de coupure publicitaire anticipée
title: Mise en oeuvre d’un retour de coupure publicitaire anticipée
uuid: 41b70ee1-290b-4732-899e-32b234ec1d9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mise en oeuvre d’un retour de coupure publicitaire anticipée {#implement-an-early-ad-break-return}

Pour l’insertion d’une publicité en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.

Par exemple, la durée de la coupure publicitaire dans certains sportifs peut ne pas être connue avant le  de coupure. TVSDK fournit une durée par défaut, mais si le jeu reprend avant la fin de la pause, la coupure publicitaire doit être quittée. Un autre exemple est un signal d’urgence pendant une coupure publicitaire dans un flux en direct.

1. Abonnez-vous aux marqueurs d’annonce de début/fin ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`et `#EXT-X-CUE`).

   Pour plus d’informations sur la manière de diviser/dans les marqueurs publicitaires, voir [Générateurs d’opportunités et résolveurs](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-content-resolver-about.md)de contenu.
1. Utilisez une personnalisation `ContentFactory`.
1. Dans `retrieveGenerators()`, utilisez le `SpliceInPlacementOpportunityGenerator`.

   Par exemple :

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Pour plus d’informations sur l’utilisation d’un détecteur personnalisé `ContentFactory`, voir l’étape 1 dans [Mise en oeuvre d’un détecteur](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-opp-detector-impl.md) d’opportunités personnalisé.

1. Sur la même personnalisation `ContentFactory`, implémentez `retrieveResolvers` et incluez `AuditudeResolver` et `SpliceInCustomResolver`.

   Par exemple :

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```

