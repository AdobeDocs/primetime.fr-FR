---
description: TVSDK fournit des informations qui vous permettent d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur de votre lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.
title: Publicités cliquables
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Publicités cliquables {#clickable-ads}

TVSDK fournit des informations qui vous permettent d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur de votre lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.

Dans TVSDK pour iOS, seules les publicités linéaires peuvent être cliquées.

## Réponse aux clics sur les publicités {#section_537AF2593FDB4257B81AAE2103B0C719}

Lorsqu’un utilisateur clique sur une publicité, une bannière publicitaire compagnon ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.

1. Pour configurer un écouteur d’événement pour TVSDK et fournir les informations sur les clics publicitaires, ajoutez un observateur pour `PTMediaPlayerAdClickNotification`.

   >[!NOTE]
   >
   >Lorsqu’un utilisateur clique sur une publicité, une bannière publicitaire compagnon ou un bouton associé, TVSDK envoie cette notification, y compris des informations sur la destination du clic.

1. Surveillez les interactions des utilisateurs sur les annonces cliquables.
1. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, pour informer TVSDK, utilisez `[_player notifyClick:_currentAd.primaryAsset];`.
1. Écoute de la `PTMediaPlayerAdClickNotification` de TVSDK.
1. Pour récupérer l’URL du clic publicitaire et les informations connexes, utilisez la variable `PTMediaPlayerAdClickURLKey` .
1. Mettez la vidéo en pause.
1. Utilisez les informations sur les clics publicitaires pour afficher l’URL des clics publicitaires et les informations associées.

   >[!NOTE]
   >
   >Vous pouvez, par exemple, afficher les informations de l’une des manières suivantes :

   * Dans votre application en ouvrant l’URL du clic publicitaire dans un navigateur.

     Sur les plateformes de bureau, la zone de lecture des publicités vidéo est utilisée pour appeler les URL de clic publicitaire lors des clics de l’utilisateur.
   * Redirigez les utilisateurs vers leur navigateur Web mobile externe.

     Sur les appareils mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que le masquage et l’affichage des commandes, la mise en pause de la lecture, le passage en plein écran, etc. Sur ces périphériques, une vue distincte, telle qu’un bouton de parrainage, est utilisée pour lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire s’affichent et relancez la lecture de la vidéo.

   Par exemple :

   ```
      // Listening for click notification  
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdClick:)  
    name:PTMediaPlayerAdClickNotification object:self.player]; 
   - (void) onMediaPlayerAdClick:(NSNotification *) notification { 
      NSString *url = [notification.userInfo objectForKey:PTMediaPlayerAdClickURLKey];  
      if (url != nil) { 
          [self openBrowser:[NSURL URLWithString:url]]; 
      } 
   } 
   ```
