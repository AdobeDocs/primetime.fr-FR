---
description: L’interface de MediaPlayer encapsule les fonctionnalités et le comportement d’un lecteur multimédia.
seo-description: L’interface de MediaPlayer encapsule les fonctionnalités et le comportement d’un lecteur multimédia.
seo-title: Configuration de MediaPlayer
title: Configuration de MediaPlayer
uuid: 4b27643c-9ccd-4abb-9793-475d06ee2a88
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Configuration de MediaPlayer {#set-up-the-mediaplayer}

TVSDK fournit des outils pour la création d’une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.

Utilisez les outils de votre plate-forme pour créer un lecteur et le connecter à la vue du lecteur multimédia dans TVSDK, qui permet de lire et de gérer des vidéos. Par exemple, TVSDK fournit des méthodes de lecture et de pause. Vous pouvez créer des boutons d&#39;interface utilisateur sur votre plate-forme et définir les boutons pour appeler ces méthodes TVSDK. L&#39;interface MediaPlayer encapsule les fonctionnalités et le comportement d&#39;un lecteur multimédia.

TVSDK fournit une implémentation unique de l’interface `MediaPlayer` : la classe DefaultMediaPlayer. Si vous avez besoin de la fonctionnalité de lecture vidéo, instanciez `DefaultMediaPlayer`.

>[!NOTE]
>
>N&#39;interagissez avec l&#39;instance `DefaultMediaPlayer` qu&#39;avec les méthodes exposées par l&#39;interface `MediaPlayer`.

1. Instanciez un `MediaPlayerContext` à l’aide de l’instance `authorizedFeatures` chargée par l’application (voir [Charger votre jeton signé](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)).

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. Instanciez un `MediaPlayer` à l’aide de la méthode public create factory, en transmettant un objet de contexte `MediaPlayerContext` :

   ```
   public static function create(context:Context):MediaPlayer
   ```

   Cette opération renvoie une interface générique `MediaPlayer`. 1. Instanciez un `MediaPlayerView` et spécifiez l’instance StageVideo à utiliser :

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. Associez l’instance `MediaPlayerView` à la nouvelle vue créée :

   ```
   mediaPlayer.view = view;
   ```

1. Placez l&#39;instance `MediaPlayerView` sur l&#39;écran du périphérique :

   ```
   container.addChild(view)
   ```

L&#39;instance `MediaPlayer` est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l&#39;écran du périphérique.