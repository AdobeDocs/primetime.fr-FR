---
description: L’interface MediaPlayer pour Android encapsule les fonctionnalités et le comportement d’un lecteur multimédia.
seo-description: L’interface MediaPlayer pour Android encapsule les fonctionnalités et le comportement d’un lecteur multimédia.
seo-title: Configuration de MediaPlayer
title: Configuration de MediaPlayer
uuid: 492b4693-acdf-4213-98e5-d6f0f1ae086d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Configuration de MediaPlayer {#set-up-the-mediaplayer}

L’interface MediaPlayer pour Android encapsule les fonctionnalités et le comportement d’un lecteur multimédia.

TVSDK fournit une implémentation de l&#39;interface `MediaPlayer`, la classe `DefaultMediaPlayer`. Si vous avez besoin de la fonctionnalité de lecture vidéo, instanciez `DefaultMediaPlayer`.

>[!TIP]
>
>N&#39;interagissez avec l&#39;instance `DefaultMediaPlayer` qu&#39;avec les méthodes exposées par l&#39;interface `MediaPlayer`.

1. Instanciez MediaPlayer à l’aide de la méthode d’usine publique `DefaultMediaPlayer.create`, en transmettant un objet contextuel d’application Java Android.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Appelez `MediaPlayer.getView` pour obtenir une référence à l&#39;instance `MediaPlayerView`.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Placez l’instance `MediaPlayerView` dans une instance `FrameLayout`, qui place la vidéo sur l’écran du périphérique.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

L&#39;instance `MediaPlayer` est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l&#39;écran du périphérique.
