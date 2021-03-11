---
description: Vous pouvez mettre en oeuvre vos propres détecteurs d'opportunités en implémentant l'interface PlacementOpportunityDetector.
title: Mise en oeuvre d'un détecteur d'opportunités personnalisé
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---


# Implémenter un détecteur d&#39;opportunités personnalisé {#implement-a-custom-opportunity-detector}

Vous pouvez mettre en oeuvre vos propres détecteurs d&#39;opportunités en implémentant l&#39;interface PlacementOpportunityDetector.

1. Créez une instance `AdvertisingFactory` personnalisée et remplacez `createOpportunityDetector`. Par exemple :

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

1. Enregistrez la fabrique du client publicitaire dans `MediaPlayer`. Par exemple :

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Créez une classe de détecteur d&#39;opportunités personnalisée qui étend la classe `PlacementOpportunityDetector`.
   1. Dans le détecteur d&#39;opportunités personnalisé, remplacez cette fonction :

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      Le `timedMetadataList` contient la liste de `TimedMetadata` disponible, qui est triée. Les métadonnées contiennent les paramètres de ciblage et les paramètres personnalisés à envoyer au fournisseur d’annonces.

   1. Pour chaque `TimedMetadata`, créez un `List<PlacementOpportunity>`. La liste peut être vide, mais pas nulle. `PlacementOpportunity` doivent avoir les attributs suivants :

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. Après avoir créé des opportunités de placement pour tous les objets de métadonnées minutés détectés, renvoyez simplement la liste `PlacementOpportunity`.

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

