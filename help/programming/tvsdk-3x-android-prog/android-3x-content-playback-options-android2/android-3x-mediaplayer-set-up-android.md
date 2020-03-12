---
description: TVSDK fournit des outils pour la création d’une application de lecteur vidéo avancée (votre lecteur Primetime) que vous pouvez intégrer à d’autres composants Primetime. Il offre également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.
seo-description: TVSDK fournit des outils pour la création d’une application de lecteur vidéo avancée (votre lecteur Primetime) que vous pouvez intégrer à d’autres composants Primetime. Il offre également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.
seo-title: Configuration du lecteur multimédia
title: Configuration du lecteur multimédia
uuid: 1f672484-b340-4f92-8a47-dad4c9f3b3fc
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Configuration du lecteur multimédia {#set-up-the-media-player}

TVSDK fournit des outils pour la création d’une application de lecteur vidéo avancée (votre lecteur Primetime) que vous pouvez intégrer à d’autres composants Primetime. Il offre également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

Instanciez un `MediaPlayer` modèle et importez-en un  dans une disposition de cadre.

1. Instanciez `MediaPlayer`, en transmettant un `android.content.Context` objet au constructeur :

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Fournissez une disposition de cadre ( `android.widget.FrameLayout`) pour contenir un `ViewGroup` nombre de `mediaPlayer`:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   >[!NOTE]
   >
   >Vous trouverez ci-dessous le fragment de code à créer `_viewGroup`.

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

   >[!NOTE]
   >
   >L’ `MediaPlayer` instance ( `mediaPlayer`) est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l’écran du périphérique.