---
description: La définition de l’interface de diffusion publicitaire du lecteur vidéo (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre une expérience multimédia riche aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
title: Prise en charge des publicités VPAID 2.0
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Prise en charge des publicités VPAID 2.0 {#vpaid-ad-support}

La définition de l’interface de diffusion publicitaire du lecteur vidéo (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre une expérience multimédia riche aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.

Les fonctionnalités suivantes sont prises en charge :

* Version 2.0 de la spécification VPAID

  Pour plus d’informations, voir [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Publicités VPAID linéaires sur le contenu vidéo à la demande (VOD)
* Publicités JavaScript VPAID

  Les publicités VPAID doivent être basées sur JavaScript et la réponse publicitaire doit identifier le type de média de la publicité VPAID comme `application/javascript`.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Version 1.0 de la spécification VPAID
* Publicités ignorables
* Publicités non linéaires telles que les publicités superposées, les publicités compagnons dynamiques, les publicités minimalisables, les publicités réductibles et les publicités extensibles
* Préchargement des publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID Flash
* Publicité VPAID post-roll

## Modifications des API {#section_D62F3E059C6C493592D34534B0BFC150}

Les modifications suivantes ont été apportées à l’API :

* `PTAuditudeMetadata` a une `customAdLoadTimeout` pour modifier le délai d’expiration par défaut sur le processus de chargement VPAID.

  La valeur par défaut du délai d’expiration est de 10 secondes.

* `PTMediaPlayerCustomAdNotification` est distribué à partir de la fonction `PTMediaPlayer` instance

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Pendant la lecture de la publicité VPAID :

* La publicité VPAID s’affiche dans un conteneur d’affichage au-dessus de la vue du lecteur, de sorte que le code qui repose sur les clics des utilisateurs sur la vue du lecteur ne fonctionne pas.
* Le lecteur de contenu principal est suspendu et appelle la fonction `pause` et `play` sur l’instance de lecteur sont utilisées pour suspendre et reprendre la publicité VPAID.

* Les publicités VPAID n’ont pas de durée prédéfinie, car elles peuvent être interactives.

  La durée de la publicité et la durée totale de coupure publicitaire définies par la réponse du serveur de publicités peuvent ne pas être exactes.

## Mise en oeuvre de l’intégration VPAID 2.0 {#section_63C9C737367C4A0AB4D62E0DC2084141}

Pour ajouter la prise en charge de VPAID 2.0 à votre application iOS :

1. (Facultatif) Ajoutez un écouteur pour les événements publicitaires personnalisés.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerCustomAdNotification:) name:PTMediaPlayerCustomAdNotification object:self.player];
   ```

1. (Facultatif) Affichez la notification.

   ```
   -(void)onMediaPlayerCustomAdNotification:(NSNotification *)notification{    PTCustomAdNotificationObject *notificationObject = [notification.userInfo objectForKey:PTCustomAdNotificationObjectKey];    if (notificationObject)    
   {        NSLog(@"ViewController:: Custom Ad Notification Received: %ld", notificationObject.type);    } 
   
   }
   ```
