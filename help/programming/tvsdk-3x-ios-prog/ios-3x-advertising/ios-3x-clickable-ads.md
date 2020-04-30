---
description: TVSDK fournit des informations vous permettant d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.
seo-description: TVSDK fournit des informations vous permettant d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.
seo-title: Publicités cliquables
title: Publicités cliquables
uuid: 8b257483-8b90-47cf-be2a-095b6d5b8883
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Publicités cliquables {#clickable-ads}

TVSDK fournit des informations vous permettant d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.

Dans TVSDK pour iOS, seules les publicités linéaires peuvent être cliquées.

## Répondre aux clics sur les publicités {#section_537AF2593FDB4257B81AAE2103B0C719}

Lorsqu’un utilisateur clique sur une publicité, une bannière publicitaire associée ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.

1. Pour configurer un écouteur de événement pour TVSDK et fournir les informations de clic publicitaire, ajoutez un observateur pour `PTMediaPlayerAdClickNotification`.

   >[!NOTE]
   >
   >Lorsqu’un utilisateur clique sur une publicité, une bannière publicitaire associée ou un bouton associé, TVSDK envoie cette notification, y compris des informations sur la destination du clic.

1. Surveillez les interactions des utilisateurs sur les annonces cliquables.
1. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, pour avertir TVSDK, utilisez `[_player notifyClick:_currentAd.primaryAsset];`.
1. Prêtez attention au `PTMediaPlayerAdClickNotification` événement de TVSDK.
1. Pour récupérer l’URL de clic publicitaire et les informations connexes, utilisez l’ `PTMediaPlayerAdClickURLKey` objet.
1. Mettez la vidéo en pause.
1. Utilisez les informations de clic publicitaire pour afficher l’URL de clic publicitaire et les informations associées.

   >[!NOTE]
   >
   >Vous pouvez, par exemple, afficher les informations de l’une des manières suivantes :

   * Dans votre application en ouvrant l’URL de clic publicitaire dans un navigateur.

      Sur les plateformes de bureau, la zone de lecture des publicités vidéo est utilisée pour appeler des URL de clic publicitaire au moment des clics des utilisateurs.
   * Redirigez les utilisateurs vers leur navigateur Web mobile externe.

      Sur les périphériques mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que masquer et afficher les commandes, suspendre la lecture, passer en mode plein écran, etc. Sur ces périphériques, une vue distincte, telle qu’un bouton de parrainage, est utilisée pour lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire s’affichent et relancez la lecture de la vidéo.

   Par exemple :

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
