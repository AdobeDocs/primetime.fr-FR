---
description: TVSDK fournit des outils pour créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime. Il fournit également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.
title: Configuration du lecteur multimédia
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Configuration du lecteur multimédia {#set-up-the-media-player}

TVSDK fournit des outils pour créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime. Il fournit également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

Instanciation d’une `MediaPlayer` et placez une vue dans une mise en page de cadre.

1. Instanciation `MediaPlayer`, transmission d’une `android.content.Context` au constructeur :

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Mettre en page un cadre ( `android.widget.FrameLayout`) pour contenir un `ViewGroup` de `mediaPlayer`:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   >[!NOTE]
   >
   >Vous trouverez ci-dessous le fragment de code à créer. `_viewGroup`.

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. Placez une vue de `mediaPlayer` dans la mise en page du cadre :

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

   >[!NOTE]
   >
   >La variable `MediaPlayer` instance ( `mediaPlayer`) est désormais disponible et correctement configuré pour afficher le contenu vidéo sur l’écran de l’appareil.
