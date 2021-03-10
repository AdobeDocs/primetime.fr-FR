---
description: L’interface MediaPlayer pour Android encapsule les fonctionnalités et le comportement d’un lecteur multimédia.
title: Configuration de MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
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
