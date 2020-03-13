---
description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture  peut être fourni par rapport à son temps de .
seo-description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture  peut être fourni par rapport à son temps de .
seo-title: Mise en oeuvre de mises à jour de temps personnalisées
title: Mise en oeuvre de mises à jour de temps personnalisées
uuid: 303303eb-c371-4766-a1ee-806ba75b4e01
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mise en oeuvre de mises à jour de temps personnalisées{#implement-custom-time-updates}

Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture  peut être fourni par rapport à son temps de .

>[!TIP]
>
>Remplacez cette méthode uniquement si vous souhaitez définir une position de curseur de lecture différente de la position par défaut.

1. Pour remplacer la position par défaut du curseur de lecture :

   ```
   vaTrackingMetadata.currentTimeUpdateBlock = ^CMTime () { 
       NSInteger random = arc4random() % 500;  
       return CMTimeMakeWithSeconds(random, 1); 
   };
   ```

   >[!IMPORTANT]
   >
   >Dans cet exemple de code, 500 est uniquement un exemple de valeur. Vous devez utiliser une autre valeur pour la position personnalisée du curseur de lecture.

