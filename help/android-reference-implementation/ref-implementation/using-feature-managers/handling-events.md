---
description: Si l’application doit gérer les événements envoyés par le gestionnaire de fonctionnalités, elle doit enregistrer le gestionnaire dans le fichier PlayerFragment.java.
title: Gestion des événements
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 4%

---


# Gestion des événements {#handling-events}

Si l’application doit gérer les événements envoyés par le gestionnaire de fonctionnalités, elle doit enregistrer le gestionnaire dans le fichier PlayerFragment.java.

Par exemple :

```
private final AdsManager.AdsManagerEventListener adsManagerEventListener =  
  new AdsManager.AdsManagerEventListener() { 
 
    // add the ads functionality... 
 
} 
 
//Register the listener 
adsManager.addEventListener(adsManagerEventListener);
```
