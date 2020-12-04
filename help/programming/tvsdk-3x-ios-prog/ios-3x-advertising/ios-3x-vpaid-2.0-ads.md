---
description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.
seo-description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.
seo-title: Prise en charge des publicités VPAID 2.0
title: Prise en charge des publicités VPAID 2.0
uuid: b688d244-c5ac-4832-b5c2-cb25bc80ce8b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Prise en charge des publicités VPAID 2.0 {#vpaid-ad-support}

Video Player Ad-Serving Interface Definition (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.

Les fonctionnalités suivantes sont prises en charge :

* Version 2.0 de la spécification VPAID

   Pour plus d&#39;informations, consultez [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Publicités VPAID linéaires sur du contenu vidéo à la demande (VOD)
* Publicités VPAID JavaScript

   Les publicités VPAID doivent être basées sur JavaScript et la réponse publicitaire doit identifier le type de média de la publicité VPAID comme `application/javascript`.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Version 1.0 de la spécification VPAID
* Annonces ignorées
* Publicités non linéaires, telles que publicités superposées, publicités complémentaires dynamiques, publicités pouvant être réduites au minimum, publicités réductibles et publicités extensibles
* Prévisualisation de publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID Flash
* Annonce VPAID après publication

## Modifications de l&#39;API {#section_D62F3E059C6C493592D34534B0BFC150}

Les modifications suivantes ont été apportées à l’API :

* `PTAuditudeMetadata` possède une  `customAdLoadTimeout` propriété permettant de modifier le délai d’expiration par défaut sur le processus de chargement VPAID.

   Le délai d’expiration par défaut est de 10 secondes.

* `PTMediaPlayerCustomAdNotification` est distribué à partir de l’ `PTMediaPlayer` instance

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Pendant la lecture de la publicité VPAID :

* La publicité VPAID est affichée dans un conteneur de vue au-dessus de la vue du lecteur. Par conséquent, le code qui repose sur les clics effectués par les utilisateurs sur la vue du lecteur ne fonctionne pas.
* Le lecteur de contenu principal est suspendu et les appels à `pause` et `play` sur l’instance du lecteur sont utilisés pour interrompre et reprendre la publicité VPAID.

* Les publicités VPAID n’ont pas de durée prédéfinie, car elles peuvent être interactives.

   La durée de la publicité et la durée totale de la coupure publicitaire définies par la réponse du serveur publicitaire peuvent ne pas être exactes.

## Mise en oeuvre de l’intégration VPAID 2.0 {#section_63C9C737367C4A0AB4D62E0DC2084141}

Pour ajouter la prise en charge de VPAID 2.0 dans votre application iOS :

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
