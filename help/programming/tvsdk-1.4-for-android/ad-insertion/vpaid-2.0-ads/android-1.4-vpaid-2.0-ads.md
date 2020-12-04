---
description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.
seo-description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.
seo-title: Prise en charge des publicités VPAID 2.0
title: Prise en charge des publicités VPAID 2.0
uuid: 7168a6e4-9c5e-4d3a-8710-867cf98e4445
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '423'
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

## Modifications de l&#39;API {#section_D62F3E059C6C493592D34534B0BFC150}

Les modifications suivantes ont été apportées à l’API :

* Une fonction `getCustomAdView` a été ajoutée dans `MediaPlayer` et renvoie la vue Web qui effectue le rendu de la publicité VPAID.

   Pour plus d&#39;informations sur l&#39;objet `CustomAdView` renvoyé par cette fonction, voir [Références API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/index.html).

* Un événement `CUSTOM_AD` est distribué à partir de l’instance du lecteur multimédia.

   L&#39;application peut enregistrer un rappel de événement en implémentant `CustomAdEventListener`.

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` vous permet de modifier le délai d’expiration par défaut sur le processus de chargement VPAID.

   Le délai d’expiration par défaut est de 10 secondes.

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Pendant la lecture de la publicité VPAID :

* La publicité VPAID est affichée dans un conteneur de vue au-dessus de la vue du lecteur. Par conséquent, le code qui repose sur les clics effectués par les utilisateurs sur la vue du lecteur ne fonctionne pas.
* Le lecteur de contenu principal est suspendu et les appels à `pause` et `play` sur l’instance du lecteur sont utilisés pour interrompre et reprendre la publicité VPAID.

* Les publicités VPAID n’ont pas de durée prédéfinie, car elles peuvent être interactives.

   La durée de la publicité et la durée totale de la coupure publicitaire définies par la réponse du serveur publicitaire peuvent ne pas être exactes.

## Mise en oeuvre de l’intégration VPAID 2.0 {#implement-vpaid-integration}

Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue publicitaire personnalisée et des écouteurs appropriés.

Pour ajouter la prise en charge de VPAID 2.0 :

1. Ajoutez la vue publicitaire personnalisée à l’interface du lecteur.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. Ajoutez un écouteur pour les événements publicitaires personnalisés.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```
