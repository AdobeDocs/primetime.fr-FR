---
description: Vous pouvez mettre en oeuvre vos propres détecteurs d'opportunités en implémentant l'interface PlacementOpportunityDetector.
seo-description: Vous pouvez mettre en oeuvre vos propres détecteurs d'opportunités en implémentant l'interface PlacementOpportunityDetector.
seo-title: Mise en oeuvre d'un détecteur d'opportunités personnalisé
title: Mise en oeuvre d'un détecteur d'opportunités personnalisé
uuid: 012527c5-4ef0-4cd6-a9df-2fb861078a7e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mise en oeuvre d&#39;un détecteur d&#39;opportunités personnalisé {#implement-a-custom-opportunity-detector}

Vous pouvez mettre en oeuvre vos propres détecteurs d&#39;opportunités en implémentant l&#39;interface PlacementOpportunityDetector.

1. Créez une `AdvertisingFactory` instance personnalisée et remplacez `createOpportunityDetector`. Par exemple :

   ```java
   new AdvertisingFactory() { 
       ... 
       @Override 
       public PlacementOpportunityDetector createOpportunityDetector(MediaPlayerItem item) { 
           return new CustomPlacementOpportunityDetector(); 
       } 
       ... 
   }
   ```

1. Enregistrez la fabrique du client publicitaire dans le `MediaPlayer`. Par exemple :

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Créez une classe de détecteur d&#39;opportunités personnalisée qui étend la `PlacementOpportunityDetector` classe.
   1. Dans le détecteur d&#39;opportunités personnalisé, remplacez cette fonction :

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      Le `timedMetadataList` contient la liste de la disponibilité `TimedMetadata`, qui est triée. Les métadonnées contiennent les paramètres de ciblage et les paramètres personnalisés à envoyer au fournisseur d’annonces.

   1. Pour chaque `TimedMetadata`élément, créez un `List<PlacementOpportunity>`élément. La liste peut être vide, mais pas nulle. `PlacementOpportunity` doivent avoir les attributs suivants :

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. Une fois les opportunités de placement créées pour tous les objets de métadonnées minutés détectés, renvoyez simplement la `PlacementOpportunity` liste.

Voici un exemple de détecteur d&#39;opportunités de placement personnalisé :

```java
public class CustomPlacementOpportunityDetector implements PlacementOpportunityDetector { 
    ... 
    @Override 
    public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata) { 
        ... 
        List<PlacementOpportunity> opportunities = new ArrayList<PlacementOpportunity>(); 
 
        for (TimedMetadata timedMetadata : timedMetadataList) { 
 
            if (isOpportunity(timedMetadata)) {        // check if given timedMetadata should be  
                                                       // considered as an opportunity 
 
                // create an object of PlacementOpportunity and add it to the opportunities list 
                PlacementOpportunity opportunity =  
                  createPlacementOpportunity(timedMetadata, airingId, metadata); 
                Opportunities.add(opportunity); 
            } 
        } 
        return opportunities; 
    }    
    ... 
} 
```

