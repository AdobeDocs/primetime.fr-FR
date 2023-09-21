---
description: L’interface de PTMediaPlayer englobe les fonctionnalités et le comportement d’un objet de lecteur multimédia.
title: Configuration de PTMediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Configuration de PTMediaPlayer {#set-up-the-ptmediaplayer}

TVSDK fournit des outils pour créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.

Utilisez les outils de votre plateforme pour créer un lecteur et le connecter à la vue du lecteur multimédia dans TVSDK, qui dispose de méthodes de lecture et de gestion des vidéos. Par exemple, TVSDK fournit des méthodes de lecture et de pause. Vous pouvez créer des boutons d’interface utilisateur sur votre plateforme et définir les boutons pour appeler ces méthodes TVSDK.

L’interface de PTMediaPlayer englobe les fonctionnalités et le comportement d’un objet de lecteur multimédia.

Pour configurer votre `PTMediaPlayer`:

1. Récupérez l’URL du média à partir de votre interface utilisateur, par exemple, dans un champ de texte.

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. Créer `PTMetadata`.

   Supposons que votre méthode `createMetada` prépare les métadonnées (voir [Publicité](../../ios-3x-advertising/ios-3x-advertising-requirements.md)).

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. Créer `PTMediaPlayerItem` en utilisant votre `PTMetadata` instance.

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. Ajoutez des observateurs aux notifications que TVSDK distribue.

   ```
   [self addObservers]
   ```

1. Créer `PTMediaPlayer` en utilisant votre nouvelle `PTMediaPlayerItem`.

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. Définissez les propriétés sur votre lecteur.

   Voici quelques-unes des options disponibles : `PTMediaPlayer` properties:

   ```
   player.autoPlay                    = YES;  
   player.closedCaptionDisplayEnabled = YES; 
   player.videoGravity                = PTMediaPlayerVideoGravityResizeAspect;  
   player.allowsAirPlayVideo          = YES;
   ```

1. Définissez la propriété view du lecteur.

   ```
   CGRect playerRect = self.adPlayerView.frame;  
   playerRect.origin = CGPointMake(0, 0); 
   playerRect.size = CGSizeMake(self.adPlayerView.frame.size.width,  
                                self.adPlayerView.frame.size.height); 
   
   [player.view setFrame:playerRect]; 
   [player.view setAutoresizingMask:  
         ( UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight )];
   ```

1. Ajoutez la vue du lecteur dans la sous-vue de la vue actuelle.

   ```
   [self.adPlayerView  setAutoresizesSubviews:YES];  
   [self.adPlayerView addSubview:(UIView *)player.view];
   ```

1. Appeler `play` pour démarrer la lecture multimédia.

   ```
   [player play];
   ```
