---
description: TVSDK fournit des outils permettant de créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime. Il offre également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.
seo-description: TVSDK fournit des outils permettant de créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime. Il offre également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.
seo-title: Configuration du lecteur multimédia
title: Configuration du lecteur multimédia
uuid: 1f672484-b340-4f92-8a47-dad4c9f3b3fc
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Configuration du lecteur multimédia {#set-up-the-media-player}

TVSDK fournit des outils permettant de créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime. Il offre également un certain nombre de fonctionnalités conçues pour optimiser la qualité de lecture vidéo.

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

Instanciez un `MediaPlayer` et placez-en une vue dans une disposition de cadre.

1. Instanciez `MediaPlayer`, en transmettant un objet `android.content.Context` au constructeur :

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Fournissez une mise en page de cadre ( `android.widget.FrameLayout`) pour contenir un `ViewGroup` de `mediaPlayer` :

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

1. Placez une vue `mediaPlayer` dans la mise en page du cadre :

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

   >[!NOTE]
   >
   >L&#39;instance `MediaPlayer` ( `mediaPlayer`) est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l&#39;écran du périphérique.