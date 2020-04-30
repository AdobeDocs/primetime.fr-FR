---
description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime du navigateur TVSDK.
seo-description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime du navigateur TVSDK.
seo-title: Mise en oeuvre de mises à jour de temps personnalisées
title: Mise en oeuvre de mises à jour de temps personnalisées
uuid: 26a0592c-a47b-4d65-b984-5e51533dcddc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Mise en oeuvre de mises à jour de temps personnalisées{#implement-custom-time-updates}

Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime du navigateur TVSDK.

Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture du programme peut être fourni par rapport à son temps de début.

>[!TIP]
>
>Remplacez cette méthode uniquement si vous souhaitez définir une position de curseur de lecture autre que la position par défaut.

Pour remplacer la position du curseur de lecture par défaut :

```js
vaMetadata.currentTimeUpdateBlock = function() { 
       return playerPositionInSeconds; 
}; 
```

>[!IMPORTANT]
>
>Les valeurs de ce fragment de code ne sont que des exemples. Vous devez utiliser des valeurs différentes pour la position personnalisée du curseur de lecture.

