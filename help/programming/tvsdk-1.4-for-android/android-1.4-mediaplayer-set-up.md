---
description: L’interface MediaPlayer pour Android englobe les fonctionnalités et le comportement d’un lecteur multimédia.
title: Configuration de MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Configuration de MediaPlayer {#set-up-the-mediaplayer}

L’interface MediaPlayer pour Android englobe les fonctionnalités et le comportement d’un lecteur multimédia.

TVSDK fournit une implémentation de la fonction `MediaPlayer` , `DefaultMediaPlayer` classe . Lorsque vous avez besoin de la fonctionnalité de lecture vidéo, instanciez `DefaultMediaPlayer`.

>[!TIP]
>
>Interagissez avec le `DefaultMediaPlayer` uniquement avec les méthodes exposées par l’objet `MediaPlayer` .

1. Instanciation d’un lecteur multimédia à l’aide du public `DefaultMediaPlayer.create` méthode factory, transmission d’un objet contextuel d’application Java Android.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Appeler `MediaPlayer.getView` pour obtenir une référence à la variable `MediaPlayerView` instance.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Placez le `MediaPlayerView` dans une instance `FrameLayout` qui place la vidéo sur l’écran de l’appareil.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

La variable `MediaPlayer` est maintenant disponible et correctement configurée pour afficher le contenu vidéo sur l’écran de l’appareil.
