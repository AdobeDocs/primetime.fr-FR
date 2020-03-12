---
description: Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.
seo-description: Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.
seo-title: Stocker les objets de métadonnées minutés au fur et à mesure qu’ils sont distribués
title: Stocker les objets de métadonnées minutés au fur et à mesure qu’ils sont distribués
uuid: 3d0ed022-829d-474e-83a9-152caeb5b317
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Stocker les objets de métadonnées minutés au fur et à mesure qu’ils sont distribués {#store-timed-metadata-objects-as-they-are-dispatched}

Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.

Lors de l’analyse du contenu, qui se produit avant la lecture, TVSDK identifie les balises abonnées et avertit votre application de ces balises.

>[!TIP]
>
>L’heure associée à chaque `TimedMetadata` heure correspond à l’heure locale du plan de montage chronologique de lecture.

Pour stocker les objets de métadonnées minutés au moment de leur diffusion :

1. Assurez le suivi du temps de lecture actuel.
1. Faites correspondre la durée de lecture actuelle aux `TimedMetadata` objets distribués.

1. Utilisez l’ `TimedMetadata` endroit où le  du est égal au temps de lecture local actuel.

   L’exemple suivant montre comment enregistrer `TimedMetadata` des objets dans un `ArrayList`fichier.

   ```java
   private List<TimedMetadata> _timedMetadataList =  
     new ArrayList<TimedMetadata>(); 
   ... 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       ... 
       if (timedMetadata.getName().equalsIgnoreCase("#EXT-X-CUE"))  { 
           _timedMetadataList.add(timedMetadata); 
       } 
       ... 
   }
   ```

