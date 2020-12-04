---
description: Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.
seo-description: Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.
seo-title: Stocker les objets de métadonnées minutés à mesure qu’ils sont distribués
title: Stocker les objets de métadonnées minutés à mesure qu’ils sont distribués
uuid: 3d0ed022-829d-474e-83a9-152caeb5b317
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# Stocker les objets de métadonnées minutés au fur et à mesure de leur distribution {#store-timed-metadata-objects-as-they-are-dispatched}

Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.

Lors de l’analyse du contenu, qui se produit avant la lecture, TVSDK identifie les balises abonnées et avertit votre application de ces balises.

>[!TIP]
>
>L’heure associée à chaque `TimedMetadata` correspond à l’heure locale du plan de montage chronologique de lecture.

Pour stocker les objets de métadonnées minutés au moment de leur diffusion :

1. Assurez le suivi de l’heure de lecture actuelle.
1. Correspond à l’heure de lecture actuelle aux objets `TimedMetadata` distribués.

1. Utilisez `TimedMetadata` où l’heure de début est égale à l’heure de lecture locale actuelle.

   L&#39;exemple suivant montre comment enregistrer des objets `TimedMetadata` dans un `ArrayList`.

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

