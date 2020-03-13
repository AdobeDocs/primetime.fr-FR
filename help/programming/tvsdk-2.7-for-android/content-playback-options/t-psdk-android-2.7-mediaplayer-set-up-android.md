---
description: Instanciez un lecteur multimédia et importez un  de celui-ci dans une disposition de cadre.
seo-description: Instanciez un lecteur multimédia et importez un  de celui-ci dans une disposition de cadre.
seo-title: Configuration de MediaPlayer
title: Configuration de MediaPlayer
uuid: 49c3edb9-b6e2-49f8-b4aa-f230af7de6b0
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Configuration de MediaPlayer {#set-up-the-mediaplayer}

TVSDK fournit des outils pour la création d’une application de lecteur vidéo avancée (votre lecteur Primetime) que vous pouvez intégrer à d’autres composants Primetime. Il offre également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.

Instanciez un lecteur multimédia et importez un  de celui-ci dans une disposition de cadre.

1. Instanciez `MediaPlayer`, en transmettant un `android.content.Context` objet au constructeur :

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Fournissez une disposition de cadre ( `android.widget.FrameLayout`) pour contenir un `ViewGroup` nombre de `mediaPlayer`:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   Vous trouverez ci-dessous le fragment de code à créer `_viewGroup`.

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. Placez un  de `mediaPlayer` l’intérieur de la disposition du cadre :

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>L’ `MediaPlayer` instance ( `mediaPlayer`) est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l’écran du périphérique.