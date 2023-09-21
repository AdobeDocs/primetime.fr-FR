---
description: L’interface MediaPlayer englobe les fonctionnalités et le comportement d’un lecteur multimédia.
title: Configuration de MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Configuration de MediaPlayer {#set-up-the-mediaplayer}

TVSDK fournit des outils pour créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.

Utilisez les outils de votre plateforme pour créer un lecteur et le connecter à la vue du lecteur multimédia dans TVSDK, qui dispose de méthodes de lecture et de gestion des vidéos. Par exemple, TVSDK fournit des méthodes de lecture et de pause. Vous pouvez créer des boutons d’interface utilisateur sur votre plateforme et définir les boutons pour appeler ces méthodes TVSDK. L’interface MediaPlayer encapsule les fonctionnalités et le comportement d’un lecteur multimédia.

TVSDK fournit une mise en oeuvre unique de `MediaPlayer` interface : classe DefaultMediaPlayer . Lorsque vous avez besoin de la fonctionnalité de lecture vidéo, instanciez `DefaultMediaPlayer`.

>[!NOTE]
>
>Interagissez avec le `DefaultMediaPlayer` uniquement avec les méthodes exposées par la fonction `MediaPlayer` .

1. Instanciation d’une `MediaPlayerContext` en utilisant l’application chargée `authorizedFeatures` instance (voir [Chargement de votre jeton signé](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)).

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. Instanciation d’une `MediaPlayer` à l’aide de la méthode public create factory, transmission d’une `MediaPlayerContext` objet context :

   ```
   public static function create(context:Context):MediaPlayer
   ```

   Cela renvoie un générique `MediaPlayer` . 1. Instanciation d’une `MediaPlayerView` et spécifiez l’instance StageVideo à utiliser :

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. Associez la variable `MediaPlayerView` avec la vue nouvellement créée :

   ```
   mediaPlayer.view = view;
   ```

1. Placez le `MediaPlayerView` sur l’écran de l’appareil :

   ```
   container.addChild(view)
   ```

La variable `MediaPlayer` est maintenant disponible et correctement configurée pour afficher le contenu vidéo sur l’écran de l’appareil.
