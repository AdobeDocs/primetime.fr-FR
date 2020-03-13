---
description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
seo-description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
seo-title: Prise en charge des publicités VPAID 2.0
title: Prise en charge des publicités VPAID 2.0
uuid: 7168a6e4-9c5e-4d3a-8710-867cf98e4445
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Prise en charge des publicités VPAID 2.0 {#vpaid-ad-support}

Video Player Ad-Serving Interface Definition (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.

Les fonctionnalités suivantes sont prises en charge :

* Version 2.0 de la spécification VPAID

   Pour plus d&#39;informations, consultez [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Annonces VPAID linéaires sur du contenu vidéo à la demande (VOD)
* Publicités VPAID JavaScript

   Les publicités VPAID doivent être basées sur JavaScript et la réponse de la publicité doit identifier le type de média de la publicité VPAID comme `application/javascript`étant.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Version 1.0 de la spécification VPAID
* Publicités ignorables
* Annonces non linéaires, telles que publicités superposées, annonces compagnons dynamiques, publicités réduites, publicités réductibles et annonces extensibles
* Préchargement de publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID Flash

## Modifications de l’API {#section_D62F3E059C6C493592D34534B0BFC150}

Les modifications suivantes ont été apportées à l’API :

* Une `getCustomAdView` fonction a été ajoutée dans `MediaPlayer` et renvoie le Web qui effectue le rendu de la publicité VPAID.

   Pour plus d’informations sur l’ `CustomAdView` objet renvoyé par cette fonction, voir Références [](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/index.html)API.

* Un `CUSTOM_AD` est distribué à partir de l’instance du lecteur multimédia.

   L’application peut enregistrer un rappel de  en implémentant `CustomAdEventListener`.

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` vous permet de modifier le délai d’expiration par défaut lors du processus de chargement VPAID.

   Le délai d’expiration par défaut est de 10 secondes.

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Pendant la lecture de la publicité VPAID :

* La publicité VPAID s’affiche dans un   au-dessus de la  du lecteur, de sorte que le code qui s’appuie sur les clics des utilisateurs sur le du lecteur ne fonctionne pas.
* Le lecteur de contenu principal est en pause et les appels vers `pause` et `play` l’instance du lecteur sont utilisés pour mettre en pause et reprendre la publicité VPAID.

* Les publicités VPAID n’ont pas de durée prédéfinie, car elles peuvent être interactives.

   La durée de la publicité et la durée totale de la coupure publicitaire définies par la réponse du serveur publicitaire peuvent ne pas être exactes.

## Mise en oeuvre de l’intégration VPAID 2.0 {#implement-vpaid-integration}

Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.

Pour ajouter la prise en charge de VPAID 2.0 :

1. Ajouter le publicitaire personnalisé  à l’interface du lecteur.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. Ajouter un écouteur pour les  publicitaires personnalisées.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```
