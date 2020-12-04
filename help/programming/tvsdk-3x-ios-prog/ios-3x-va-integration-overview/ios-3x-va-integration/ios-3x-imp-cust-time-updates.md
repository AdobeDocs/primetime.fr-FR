---
description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture du programme peut être fourni par rapport à son temps de début.
seo-description: Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture du programme peut être fourni par rapport à son temps de début.
seo-title: Mise en oeuvre de mises à jour de temps personnalisées
title: Mise en oeuvre de mises à jour de temps personnalisées
uuid: 174937ca-3c26-4385-a298-8a01fc93ea20
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Mettre en oeuvre des mises à jour de temps personnalisées {#implement-custom-time-updates}

Dans certaines implémentations d’analyse, l’application cliente peut souhaiter fournir une position de curseur de lecture différente de celle rapportée par la valeur localTime de TVSDK. Par exemple, pendant la lecture d’un flux linéaire, chaque curseur de lecture du programme peut être fourni par rapport à son temps de début.

>[!TIP]
>
>Remplacez cette méthode uniquement si vous souhaitez fournir une position de curseur de lecture différente de la position par défaut.

Pour remplacer la position du curseur de lecture par défaut :

```
vaTrackingMetadata.currentTimeUpdateBlock = ^CMTime () { 
    NSInteger random = arc4random() % 500;  
    return CMTimeMakeWithSeconds(random, 1); 
};
```

>[!IMPORTANT]
>
>Dans cet exemple de code, 500 est seulement un exemple de valeur. Vous devez utiliser une autre valeur pour la position personnalisée du curseur de lecture.