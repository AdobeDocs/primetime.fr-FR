---
description: Création du gestionnaire d’analyses vidéo
seo-description: Création du gestionnaire d’analyses vidéo
seo-title: Création du gestionnaire d’analyses vidéo
title: Création du gestionnaire d’analyses vidéo
uuid: d72e1dfe-df70-47cc-9e00-bd09017d6127
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Création du gestionnaire d’analyses vidéo {#create-the-video-analytics-manager}

Une nouvelle classe manager ( `VAManager`) a été ajoutée à l&#39;implémentation de référence Android. `VAManager` crée et détruit simplement une instance de la  `VideoHeartbeat` classe. L&#39;implémentation de référence crée une instance `VAManager` lorsqu&#39;une nouvelle instance `MediaPlayer` est créée et détruit cette instance lorsque l&#39;instance `MediaPlayer` est détruite. Ceci est implémenté dans `PlayerFragment.java`.

## Pour créer un gestionnaire d’analyses vidéo

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

La variable de configuration est une implémentation concrète de `IVAConfig` et contient les configurations d&#39;exécution `VideoHeartbeat`.

>[!NOTE]
>
>Si l&#39;application Android n&#39;est pas configurée avec un compte Adobe Analytics, les données de suivi vidéo ne seront pas générées, même si une instance de `VAManager` est créée et activée.

