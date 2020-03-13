---
description: La version 2.0 de l’interface VPAID (Video Player Ad Serving Interface Definition) fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
seo-description: La version 2.0 de l’interface VPAID (Video Player Ad Serving Interface Definition) fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
seo-title: Prise en charge des publicités VPAID 2.0
title: Prise en charge des publicités VPAID 2.0
uuid: 462692b5-c4b3-4488-adb3-f309809d64ad
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Prise en charge des publicités VPAID 2.0 {#vpaid-ad-support}

La version 2.0 de l’interface VPAID (Video Player Ad Serving Interface Definition) fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.

Les fonctionnalités suivantes sont prises en charge :

* Version 2.0 de la spécification VPAID

   Pour plus d’informations, voir [IAB VPAID 2.0](https://www.iab.com/guidelines/digital-video-player-ad-interface-definition-vpaid-2-0/).
* Annonces VPAID linéaires avec contenu vidéo à la demande (VOD)
* Dans le contenu en direct, le navigateur TVSDK prend en charge les annonces VPAID JavaScript preroll.
* En mode de secours Flash, le navigateur TVSDK ne prend en charge que les annonces VPAID Flash.
* Annonces VPAID JavaScript linéaires

   Les publicités VPAID doivent être basées sur JavaScript et la réponse de la publicité doit identifier le type de média de la publicité VPAID comme `application/javascript`étant.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Version 1.0 de la spécification VPAID
* Publicités ignorables
* Annonces non linéaires, telles que publicités superposées, annonces compagnons dynamiques, publicités minimalisables, publicités réductibles et annonces extensibles.
* Préchargement de publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID Flash

## API {#section_0DB1D383CA5047B281BC808BC082C69B}

Les éléments d’API suivants prennent en charge les annonces VPAID 2.0 :

* La `getCustomAdView` méthode de `MediaPlayer` renvoie un `CustomAdView` objet, qui représente le Web qui effectue le rendu de la publicité VPAID.

   Pour plus d’informations sur la `getCustomAdView` méthode, voir la documentation [de l’API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.MediaPlayer.html)MediaPlayer.

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` définit le délai d’expiration sur le processus de chargement VPAID.

   Le délai d’expiration par défaut est de 10 secondes.

* L’API `auditudeSettings.ignoreVPAIDAds`, vous permet d’ignorer les publicités VPAID reçues du serveur Auditude. L’API ne fonctionne pas pour les abandons Flash.

Pendant la lecture de la publicité VPAID :

* La publicité VPAID s’affiche dans un   au-dessus de la  du lecteur, de sorte que le code qui s’appuie sur les clics des utilisateurs sur le du lecteur ne fonctionne pas.
* Appels à la mise en pause et à la lecture sur l’instance du lecteur, à la mise en pause et à la reprise de la publicité VPAID.
* Les publicités VPAID n’ont pas de durée prédéfinie, car elles peuvent être interactives.

   La durée de la publicité et la durée totale de la coupure publicitaire spécifiées dans la réponse du serveur publicitaire peuvent ne pas être exactes.