---
description: Dans certaines mises en oeuvre d’analyse, l’application client peut souhaiter fournir une position de curseur de lecture différente de celle signalée par la valeur localTime de TVSDK. Par exemple, lors d’une lecture de flux linéaire, le curseur de lecture de chaque programme peut être fourni par rapport à son heure de début.
title: Mise en oeuvre de mises à jour d’heure personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Mise en oeuvre de mises à jour d’heure personnalisées {#implement-custom-time-updates}

Dans certaines mises en oeuvre d’analyse, l’application client peut souhaiter fournir une position de curseur de lecture différente de celle signalée par la valeur localTime de TVSDK. Par exemple, lors d’une lecture de flux linéaire, le curseur de lecture de chaque programme peut être fourni par rapport à son heure de début.

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
