---
description: Instanciez un MediaPlayer et placez-en une vue dans une mise en page de cadre.
seo-description: Instanciez un MediaPlayer et placez-en une vue dans une mise en page de cadre.
seo-title: Configuration de MediaPlayer
title: Configuration de MediaPlayer
uuid: 49c3edb9-b6e2-49f8-b4aa-f230af7de6b0
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Configuration de MediaPlayer {#set-up-the-mediaplayer}

TVSDK fournit des outils permettant de créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime. Il offre également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.

Instanciez un MediaPlayer et placez-en une vue dans une mise en page de cadre.

1. Instanciez `MediaPlayer`, en transmettant un objet `android.content.Context` au constructeur :

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Fournissez une mise en page de cadre ( `android.widget.FrameLayout`) pour contenir un `ViewGroup` de `mediaPlayer` :

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

1. Placez une vue `mediaPlayer` dans la mise en page du cadre :

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>L&#39;instance `MediaPlayer` ( `mediaPlayer`) est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l&#39;écran du périphérique.