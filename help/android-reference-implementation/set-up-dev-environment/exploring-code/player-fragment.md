---
description: La classe PlayerFragment permet de modifier le code pour créer les gestionnaires de fonctionnalités entièrement activés.
title: PlayerFragment
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# PlayerFragment {#playerfragment}

La classe PlayerFragment permet de modifier le code pour créer les gestionnaires de fonctionnalités entièrement activés.

La variable `PlayerFragment` contient tous les composants de l’interface utilisateur, tels que le `playerFrame`, `ControlBar`, `playerClickableAdFragment`, et `adOverlay`.

Il gère l’initialisation de tous ces composants, ainsi que la création du lecteur, la configuration des vues, la création de gestionnaires de fonctionnalités pour le lecteur multimédia, la gestion des événements multimédias tels que la reprise, la lecture et la mise en pause et la gestion des écouteurs d’événements pour `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `AdsManager`, `PlaybackManager`, et `EntitlementManager`.

Le fichier XML qui comprend les paramètres de configuration pour la variable `PlayerFragment` is `res/layout/fragment_player.xml`.

Avant de créer les gestionnaires de fonctionnalités, vous devez créer le lecteur multimédia en vous assurant que le code suivant figure dans la variable `PlayerFragment.java` fichier :

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
