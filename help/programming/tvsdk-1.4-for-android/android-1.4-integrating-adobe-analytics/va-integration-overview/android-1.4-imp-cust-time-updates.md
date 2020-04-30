---
description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture du programme peut être fourni par rapport à son temps de début.
seo-description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture du programme peut être fourni par rapport à son temps de début.
seo-title: Mise en oeuvre de mises à jour de temps personnalisées
title: Mise en oeuvre de mises à jour de temps personnalisées
uuid: 7f5d46e5-eab6-4bdc-b015-ae27ddb609ce
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mise en oeuvre de mises à jour de temps personnalisées {#implement-custom-time-updates}

Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture du programme peut être fourni par rapport à son temps de début.

>[!TIP]
>
>Remplacez cette méthode uniquement si vous souhaitez définir une position de curseur de lecture autre que la position par défaut.

Pour remplacer la position du curseur de lecture par défaut :

```java
vaMetadata.setCurrentTimeUpdateBlock(new VideoAnalyticsMetadata.CurrentTimeUpdateBlock() { 
    @Override 
    public long call() { 
        long range = 500L; 
        Random r = new Random() 
        return (long)(r.nextDouble()*range); 
    } 
});
```

>[!IMPORTANT]
>
>Les valeurs de ce fragment de code ne sont que des exemples. Vous devez utiliser des valeurs différentes pour la position personnalisée du curseur de lecture.