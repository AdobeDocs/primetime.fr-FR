---
description: Création de Video Analytics Manager
title: Création de Video Analytics Manager
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Création de Video Analytics Manager {#create-the-video-analytics-manager}

Une nouvelle classe de gestionnaire ( `VAManager`) a été ajouté à l’implémentation de référence Android. `VAManager` crée et détruit simplement une instance de la fonction `VideoHeartbeat` classe . L’implémentation de référence crée une `VAManager` lorsqu’une nouvelle instance `MediaPlayer` est créé et détruit cette instance lorsque la fonction `MediaPlayer` est détruite. Cela est implémenté dans `PlayerFragment.java`.

## Pour créer un gestionnaire d’analyses vidéo

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

La variable config est une mise en oeuvre concrète de la variable `IVAConfig` et contient l’exécution `VideoHeartbeat` configurations.

>[!NOTE]
>
>Si l’application Android n’est pas configurée avec un compte Adobe Analytics, les données de suivi vidéo ne sont pas générées, même si une instance de `VAManager` est créée et activée.
