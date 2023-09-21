---
description: Dans certaines mises en oeuvre d’analyse, l’application client peut souhaiter fournir une position de curseur de lecture différente de celle signalée par la valeur localTime de TVSDK. Par exemple, lors d’une lecture de flux LINEAR, le curseur de lecture de chaque programme peut être fourni par rapport à son heure de début.
title: Mise en oeuvre de mises à jour d’heure personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Mise en oeuvre de mises à jour d’heure personnalisées{#implement-custom-time-updates}

Dans certaines mises en oeuvre d’analyse, l’application client peut souhaiter fournir une position de curseur de lecture différente de celle signalée par la valeur localTime de TVSDK. Par exemple, lors d’une lecture de flux LINEAR, le curseur de lecture de chaque programme peut être fourni par rapport à son heure de début.

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
