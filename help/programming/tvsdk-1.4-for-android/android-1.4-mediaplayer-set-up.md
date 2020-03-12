---
description: L’interface MediaPlayer pour Android encapsule la fonctionnalité et le comportement d’un lecteur multimédia.
seo-description: L’interface MediaPlayer pour Android encapsule la fonctionnalité et le comportement d’un lecteur multimédia.
seo-title: Configuration de MediaPlayer
title: Configuration de MediaPlayer
uuid: 492b4693-acdf-4213-98e5-d6f0f1ae086d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Configuration de MediaPlayer {#set-up-the-mediaplayer}

L’interface MediaPlayer pour Android encapsule la fonctionnalité et le comportement d’un lecteur multimédia.

TVSDK fournit une implémentation de l’ `MediaPlayer` interface, la `DefaultMediaPlayer` classe. Lorsque vous avez besoin de la fonctionnalité de lecture vidéo, instanciez `DefaultMediaPlayer`.

>[!TIP]
>
>Interagissez avec l’ `DefaultMediaPlayer` instance uniquement avec les méthodes exposées par l’ `MediaPlayer` interface.

1. Instanciez un lecteur multimédia à l’aide de la méthode `DefaultMediaPlayer.create` usine publique, en transmettant un objet de contexte d’application Java Android.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Appelez `MediaPlayer.getView` pour obtenir une référence à l’ `MediaPlayerView` instance.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Placez l’ `MediaPlayerView` instance dans une `FrameLayout` instance qui place la vidéo sur l’écran du périphérique.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

L’ `MediaPlayer` instance est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l’écran du périphérique.
