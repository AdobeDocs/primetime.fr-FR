---
description: Si l’application doit gérer les  distribués à partir du gestionnaire de fonctionnalités, elle doit enregistrer le gestionnaire dans le fichier PlayerFragment.java.
seo-description: Si l’application doit gérer les  distribués à partir du gestionnaire de fonctionnalités, elle doit enregistrer le gestionnaire dans le fichier PlayerFragment.java.
seo-title: 'Gestion des '
title: 'Gestion des '
uuid: 13639f02-0dcc-4a0a-8524-515da5478006
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Gestion des {#handling-events}

Si l’application doit gérer les  distribués à partir du gestionnaire de fonctionnalités, elle doit enregistrer le gestionnaire dans le fichier PlayerFragment.java.

Par exemple :

```
private final AdsManager.AdsManagerEventListener adsManagerEventListener =  
  new AdsManager.AdsManagerEventListener() { 
 
    // add the ads functionality... 
 
} 
 
//Register the listener 
adsManager.addEventListener(adsManagerEventListener);
```
