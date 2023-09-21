---
description: Pour l’insertion de publicités en continu, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
title: Mise en oeuvre d’un retour de coupure publicitaire anticipée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Mise en oeuvre d’un retour de coupure publicitaire anticipée {#implement-an-early-ad-break-return}

Pour l’insertion de publicités en continu, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.

Par exemple, la durée de la coupure publicitaire dans certains événements sportifs peut ne pas être connue avant le début de la coupure. TVSDK fournit une durée par défaut, mais si le jeu reprend avant que la coupure ne se termine, la coupure publicitaire doit être quittée. Un autre exemple est un signal d’urgence pendant une coupure publicitaire dans un flux en direct.

1. Abonnez-vous aux marqueurs publicitaires sortants/intégrés ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`, et `#EXT-X-CUE`).

   Pour plus d’informations sur la manière de diviser/dans les marqueurs d’annonce, voir [Générateurs d’opportunités et programmes de résolution de contenu](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-content-resolver-about.md).
1. Utilisation d’une `ContentFactory`.
1. Dans `retrieveGenerators()`, utilisez le `SpliceInPlacementOpportunityGenerator`.

   Par exemple :

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Pour plus d’informations sur l’utilisation d’un `ContentFactory`, voir l’étape 1 dans [Mise en oeuvre d’un détecteur d’opportunités personnalisé](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-opp-detector-impl.md) .

1. Sur la même `ContentFactory`, implémenter `retrieveResolvers` et inclure `AuditudeResolver` et `SpliceInCustomResolver`.

   Par exemple :

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
