---
description: Vous pouvez implémenter vos propres détecteurs d’opportunités en implémentant l’interface PlacementOpportunityDetector.
title: Mise en oeuvre d’un détecteur d’opportunités personnalisé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Mise en oeuvre d’un détecteur d’opportunités personnalisé {#implement-a-custom-opportunity-detector}

Vous pouvez implémenter vos propres détecteurs d’opportunités en implémentant l’interface PlacementOpportunityDetector.

1. Création d’une `AdvertisingFactory` instance et remplacement `createOpportunityDetector`. Par exemple :

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

1. Enregistrez la fabrique de clients d’annonces sur la page `MediaPlayer`. Par exemple :

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Créez une classe de détecteur d’opportunités personnalisée qui étend la variable `PlacementOpportunityDetector` classe .
   1. Dans le détecteur d’opportunités personnalisé, remplacez cette fonction :

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      La variable `timedMetadataList` contient la liste des `TimedMetadata`, qui est triée. Les métadonnées contiennent les paramètres de ciblage et les paramètres personnalisés à envoyer au fournisseur de publicités.

   1. Pour chaque `TimedMetadata`, créez un `List<PlacementOpportunity>`. La liste peut être vide, mais pas nulle. `PlacementOpportunity` doivent avoir les attributs suivants :

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. Une fois les opportunités d’emplacement créées pour tous les objets de métadonnées minutés détectés, renvoyez simplement la variable `PlacementOpportunity` liste.

Voici un exemple de détecteur d’opportunités d’emplacement personnalisé :

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
