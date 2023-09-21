---
description: Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.
title: Stocker les objets de métadonnées minutés lors de leur distribution
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# Stocker les objets de métadonnées minutés lors de leur distribution {#store-timed-metadata-objects-as-they-are-dispatched}

Votre application doit utiliser les objets TimedMetadata appropriés aux moments appropriés.

Pendant l’analyse du contenu, qui se produit avant la lecture, TVSDK identifie les balises abonnées et informe votre application de ces balises.

>[!TIP]
>
>L’heure associée à chaque `TimedMetadata` correspond à l’heure locale de la chronologie de lecture.

Pour stocker les objets de métadonnées minutés au fur et à mesure qu’ils sont distribués :

1. Effectuez le suivi de la durée de lecture actuelle.
1. Correspondance de la durée de lecture actuelle avec le délai distribué `TimedMetadata` objets.

1. Utilisez la variable `TimedMetadata` où l’heure de début est égale à l’heure de lecture locale actuelle.

   L’exemple suivant montre comment enregistrer `TimedMetadata` dans un objet `ArrayList`.

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
