---
description: Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.
seo-description: Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.
seo-title: Stocker les objets de métadonnées minutés à mesure qu’ils sont distribués
title: Stocker les objets de métadonnées minutés à mesure qu’ils sont distribués
uuid: 0d0ddfea-6f32-467d-91bc-f18ceadcd842
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Stocker les objets de métadonnées minutés à mesure qu’ils sont distribués {#store-timed-metadata-objects-as-they-are-dispatched}

Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.

Lors de l’analyse du contenu, qui se produit avant la lecture, TVSDK identifie les balises abonnées et avertit votre application de ces balises.

>[!TIP]
>
>L’heure associée à chaque `TimedMetadata` heure correspond à l’heure locale du plan de montage chronologique de lecture.

Pour stocker les objets de métadonnées minutés au moment de leur diffusion :

1. Assurez le suivi de l’heure de lecture actuelle.
1. Correspond à l’heure de lecture actuelle aux `TimedMetadata` objets distribués.

1. Utilisez l’ `TimedMetadata` endroit où l’heure de début est égale à l’heure de lecture locale actuelle.

   L&#39;exemple suivant montre comment enregistrer `TimedMetadata` des objets dans un `ArrayList`objet.

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

