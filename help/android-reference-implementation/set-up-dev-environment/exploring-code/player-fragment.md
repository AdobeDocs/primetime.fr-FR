---
description: La classe PlayerFragment permet de modifier le code pour créer les gestionnaires de fonctionnalités entièrement activés.
seo-description: La classe PlayerFragment permet de modifier le code pour créer les gestionnaires de fonctionnalités entièrement activés.
seo-title: PlayerFragment
title: PlayerFragment
uuid: 83f02c31-f3b1-4d16-97c8-5b391e8c999a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# PlayerFragment {#playerfragment}

La classe PlayerFragment permet de modifier le code pour créer les gestionnaires de fonctionnalités entièrement activés.

La classe `PlayerFragment` contient tous les composants de l&#39;interface utilisateur, tels que `playerFrame`, `ControlBar`, `playerClickableAdFragment` et `adOverlay`.

Il gère l&#39;initialisation de tous ces composants ainsi que la création du lecteur, la configuration des vues, la création de gestionnaires de fonctionnalités pour le lecteur multimédia, la gestion des événements de médias tels que la reprise, la lecture, la mise en pause et la gestion des écouteurs de événement pour `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `PlaybackManager` et `EntitlementManager`.`AdsManager`

Le fichier XML qui inclut les paramètres de configuration de `PlayerFragment` est `res/layout/fragment_player.xml`.

Avant de créer les gestionnaires de fonctionnalités, vous devez créer le lecteur multimédia en vous assurant que le code suivant figure dans le fichier `PlayerFragment.java` :

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
