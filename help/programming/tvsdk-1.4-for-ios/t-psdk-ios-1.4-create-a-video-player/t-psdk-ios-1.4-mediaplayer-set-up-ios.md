---
description: L’interface PTMediaPlayer encapsule la fonctionnalité et le comportement d’un objet de lecteur multimédia.
seo-description: L’interface PTMediaPlayer encapsule la fonctionnalité et le comportement d’un objet de lecteur multimédia.
seo-title: Configuration de PTMediaPlayer
title: Configuration de PTMediaPlayer
uuid: 78549406-7e33-4bca-a25e-1e433f6a75d7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Configuration de PTMediaPlayer {#set-up-the-ptmediaplayer}

TVSDK fournit des outils pour la création d’une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.

Utilisez les outils de votre plate-forme pour créer un lecteur et le connecter à la vue du lecteur multimédia dans TVSDK, qui permet de lire et de gérer des vidéos. Par exemple, TVSDK fournit des méthodes de lecture et de pause. Vous pouvez créer des boutons d’interface utilisateur sur votre plate-forme et définir les boutons pour appeler ces méthodes TVSDK.

L’interface PTMediaPlayer encapsule la fonctionnalité et le comportement d’un objet de lecteur multimédia.

Pour configurer votre `PTMediaPlayer` :

1. Récupérez l’URL du média de votre interface utilisateur, par exemple, dans un champ de texte.

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. Créez `PTMetadata`.

   Supposons que votre méthode `createMetada` prépare des métadonnées (voir [Publicité](../ad-insertion/r-psdk-ios-1.4-advertising-requirements.md)).

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. Créez `PTMediaPlayerItem` en utilisant votre instance `PTMetadata`.

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. Ajoutez des observateurs aux notifications que TVSDK envoie.

   ```
   [self addObservers]
   ```

1. Créez `PTMediaPlayer` en utilisant votre nouveau `PTMediaPlayerItem`.

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. Définissez les propriétés sur votre lecteur.

   Voici quelques-unes des propriétés `PTMediaPlayer` disponibles :

   ```
   player.autoPlay                    = YES;  
   player.closedCaptionDisplayEnabled = YES; 
   player.videoGravity                = PTMediaPlayerVideoGravityResizeAspect;  
   player.allowsAirPlayVideo          = YES;
   ```

1. Définissez la propriété de vue du lecteur.

   ```
   CGRect playerRect = self.adPlayerView.frame;  
   playerRect.origin = CGPointMake(0, 0); 
   playerRect.size = CGSizeMake(self.adPlayerView.frame.size.width,  
                                self.adPlayerView.frame.size.height); 
   
   [player.view setFrame:playerRect]; 
   [player.view setAutoresizingMask:  
         ( UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight )];
   ```

1. Ajoutez la vue du lecteur dans la sous-vue vue actuelle.

   ```
   [self.adPlayerView  setAutoresizesSubviews:YES];  
   [self.adPlayerView addSubview:(UIView *)player.view];
   ```

1. Appelez `play` pour début de la lecture multimédia.

   ```
   [player play];
   ```

