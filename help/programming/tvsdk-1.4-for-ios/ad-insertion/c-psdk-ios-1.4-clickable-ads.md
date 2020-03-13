---
description: TVSDK vous fournit des informations pour que vous puissiez agir sur les publicités par clics publicitaires. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider de la manière dont vous répondez lorsqu’un utilisateur clique sur une publicité cliquable.
seo-description: TVSDK vous fournit des informations pour que vous puissiez agir sur les publicités par clics publicitaires. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider de la manière dont vous répondez lorsqu’un utilisateur clique sur une publicité cliquable.
seo-title: Publicités cliquables
title: Publicités cliquables
uuid: dc02cba7-34ad-4c74-9ceb-2fc1050d54aa
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Publicités cliquables{#clickable-ads}

TVSDK vous fournit des informations pour que vous puissiez agir sur les publicités par clics publicitaires. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider de la manière dont vous répondez lorsqu’un utilisateur clique sur une publicité cliquable.

Dans TVSDK pour iOS, seules les publicités linéaires peuvent être cliquées.

## Répondre aux clics sur les publicités {#section_537AF2593FDB4257B81AAE2103B0C719}

Lorsqu’un utilisateur clique sur une publicité, une bannière publicitaire associée ou un bouton associé, votre application doit répondre. TVSDK vous fournit des informations sur l’URL de destination du clic.

1. Pour configurer un écouteur de  pour TVSDK et fournir les informations de clic publicitaire, ajoutez un observateur pour `PTMediaPlayerAdClickNotification`.

   >[!NOTE]
   >
   >Lorsqu’un utilisateur clique sur une publicité, une bannière publicitaire associée ou un bouton associé, TVSDK envoie cette notification, y compris des informations sur la destination du clic.

1. Surveillez les interactions des utilisateurs sur les annonces cliquables.
1. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, utilisez `[_player notifyClick:_currentAd.primaryAsset];`pour avertir TVSDK.
1. Écoutez le `PTMediaPlayerAdClickNotification` de TVSDK.
1. Pour récupérer l’URL de clic publicitaire et les informations connexes, utilisez l’ `PTMediaPlayerAdClickURLKey` objet.
1. Mettez la vidéo en pause.
1. Utilisez les informations de clic publicitaire pour afficher l’URL de clic publicitaire et les informations associées.

   >[!NOTE]
   >
   >Vous pouvez, par exemple, afficher les informations de l’une des manières suivantes :

   * Dans votre application en ouvrant l’URL du clic publicitaire dans un navigateur.

      Sur les plateformes de bureau, la zone de lecture des publicités vidéo est utilisée pour appeler les URL de clics publicitaires au moment des clics des utilisateurs.
   * Redirigez les utilisateurs vers leur navigateur Web mobile externe.

      Sur les périphériques mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que le masquage et l’affichage des commandes, la mise en pause de la lecture, le développement en plein écran, etc. Sur ces périphériques, un  distinct, tel qu’un bouton de sponsor, est utilisé pour lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire sont affichées et relancez la lecture de la vidéo.

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

