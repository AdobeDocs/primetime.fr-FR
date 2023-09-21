---
description: Si l’application doit gérer les événements distribués à partir du gestionnaire de fonctionnalités, elle doit enregistrer le gestionnaire dans le fichier PlayerFragment.java .
title: Gestion des événements
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Gestion des événements {#handling-events}

Si l’application doit gérer les événements distribués à partir du gestionnaire de fonctionnalités, elle doit enregistrer le gestionnaire dans le fichier PlayerFragment.java .

Par exemple :

```
private final AdsManager.AdsManagerEventListener adsManagerEventListener =  
  new AdsManager.AdsManagerEventListener() { 
 
    // add the ads functionality... 
 
} 
 
//Register the listener 
adsManager.addEventListener(adsManagerEventListener);
```
