---
description: Création du gestionnaire d’analyses vidéo
seo-description: Création du gestionnaire d’analyses vidéo
seo-title: Création du gestionnaire d’analyses vidéo
title: Création du gestionnaire d’analyses vidéo
uuid: d72e1dfe-df70-47cc-9e00-bd09017d6127
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Création du gestionnaire d’analyses vidéo {#create-the-video-analytics-manager}

Une nouvelle classe de gestionnaire ( `VAManager`) a été ajoutée à l’implémentation des références Android. `VAManager` crée et détruit simplement une instance de la `VideoHeartbeat` classe. L’implémentation de référence crée une `VAManager` instance lorsqu’une nouvelle `MediaPlayer` instance est créée et détruit cette instance lors de la `MediaPlayer` destruction. Ceci est mis en oeuvre dans `PlayerFragment.java`.

## Pour créer un gestionnaire d’analyses vidéo

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

La variable config est une implémentation concrète de `IVAConfig` et contient les configurations d’exécution `VideoHeartbeat` .

>[!NOTE]
>
>Si l’application Android n’est pas configurée avec un compte Adobe Analytics, les données de suivi vidéo ne sont pas générées, même si une instance de `VAManager` est créée et activée.

