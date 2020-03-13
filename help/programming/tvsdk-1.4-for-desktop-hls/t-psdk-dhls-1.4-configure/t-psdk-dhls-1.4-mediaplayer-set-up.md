---
description: L’interface MediaPlayer encapsule la fonctionnalité et le comportement d’un lecteur multimédia.
seo-description: L’interface MediaPlayer encapsule la fonctionnalité et le comportement d’un lecteur multimédia.
seo-title: Configuration de MediaPlayer
title: Configuration de MediaPlayer
uuid: 4b27643c-9ccd-4abb-9793-475d06ee2a88
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Configuration de MediaPlayer {#set-up-the-mediaplayer}

TVSDK fournit des outils pour la création d’une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.

Utilisez les outils de votre plate-forme pour créer un lecteur et le connecter au du lecteur multimédia dans TVSDK, qui dispose de méthodes pour lire et gérer les vidéos. Par exemple, TVSDK fournit des méthodes de lecture et de pause. Vous pouvez créer des boutons d&#39;interface utilisateur sur votre plateforme et définir les boutons pour appeler ces méthodes TVSDK. L&#39;interface MediaPlayer encapsule la fonctionnalité et le comportement d&#39;un lecteur multimédia.

TVSDK fournit une implémentation unique de l’ `MediaPlayer` interface : la classe DefaultMediaPlayer. Lorsque vous avez besoin de la fonctionnalité de lecture vidéo, instanciez `DefaultMediaPlayer`.

>[!NOTE]
>
>Interagissez avec l’ `DefaultMediaPlayer` instance uniquement avec les méthodes exposées par l’ `MediaPlayer` interface.

1. Instanciez une `MediaPlayerContext` instance à l’aide de l’ `authorizedFeatures` instance chargée par l’application (voir [Chargement du jeton](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)signé).

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. Instanciez une `MediaPlayer` méthode publique create factory, en transmettant un objet `MediaPlayerContext` context :

   ```
   public static function create(context:Context):MediaPlayer
   ```

   Cette opération renvoie une `MediaPlayer` interface générique. 1. Instanciez une instance `MediaPlayerView` et spécifiez l’instance StageVideo à utiliser :

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. Associez l’ `MediaPlayerView` instance au nouveau :

   ```
   mediaPlayer.view = view;
   ```

1. Placez l’ `MediaPlayerView` instance sur l’écran du périphérique :

   ```
   container.addChild(view)
   ```

L’ `MediaPlayer` instance est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l’écran du périphérique.