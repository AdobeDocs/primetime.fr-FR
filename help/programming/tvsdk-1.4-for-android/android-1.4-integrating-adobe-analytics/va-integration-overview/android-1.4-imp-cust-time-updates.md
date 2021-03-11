---
description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localeTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture du programme peut être fourni par rapport à son temps de début.
title: Mise en oeuvre de mises à jour de temps personnalisées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Mettre en oeuvre des mises à jour de temps personnalisées {#implement-custom-time-updates}

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