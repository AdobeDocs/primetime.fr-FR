---
description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime de TVSDK. Par exemple, lors de la lecture d’un flux LINEAR, chaque curseur de lecture du programme peut être fourni par rapport à son heure de début.
seo-description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime de TVSDK. Par exemple, lors de la lecture d’un flux LINEAR, chaque curseur de lecture du programme peut être fourni par rapport à son heure de début.
seo-title: Mise en oeuvre de mises à jour de temps personnalisées
title: Mise en oeuvre de mises à jour de temps personnalisées
uuid: 2b46eca9-3815-4c44-ab5e-21678c35f410
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Mise en oeuvre de mises à jour de temps personnalisées{#implement-custom-time-updates}

Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime de TVSDK. Par exemple, lors de la lecture d’un flux LINEAR, chaque curseur de lecture du programme peut être fourni par rapport à son heure de début.

>[!TIP]
>
>Remplacez cette méthode uniquement si vous souhaitez fournir une position de curseur de lecture différente de celle par défaut.

1. Pour remplacer la position du curseur de lecture par défaut :

   ```
   vaMetadata.currentTimeUpdateBlock = function():Number { 
      if (currentTime == 0) { 
          currentTime = getTimer(); 
      } 
      return ((getTimer() - currentTime) / 1000 + 1000); 
   }
   ```

   >[!IMPORTANT]
   >
   >Les valeurs de ce fragment de code ne sont que des exemples. Vous devez utiliser des valeurs différentes pour la position personnalisée du curseur de lecture.

