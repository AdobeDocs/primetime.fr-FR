---
description: La définition de l’interface de service publicitaire du lecteur vidéo (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre une expérience multimédia riche aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
title: Prise en charge des publicités VPAID 2.0
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Prise en charge des publicités VPAID 2.0 {#vpaid-ad-support}

La définition de l’interface de service publicitaire du lecteur vidéo (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre une expérience multimédia riche aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.

Les fonctionnalités suivantes sont prises en charge :

* Version 2.0 de la spécification VPAID

  Pour plus d’informations, voir [IAB VPAID 2.0](https://www.iab.com/guidelines/digital-video-player-ad-interface-definition-vpaid-2-0/).
* Publicités VPAID linéaires avec contenu vidéo à la demande (VOD)
* Dans le contenu en direct, le navigateur TVSDK prend en charge les publicités JavaScript VPAID preroll.
* En mode de secours par Flash, le TVSDK du navigateur ne prend en charge que les publicités VPAID basées sur le Flash.
* Publicités VPAID JavaScript linéaires

  Les publicités VPAID doivent être basées sur JavaScript et la réponse publicitaire doit identifier le type de média de la publicité VPAID comme `application/javascript`.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Version 1.0 de la spécification VPAID
* Publicités ignorables
* Publicités non linéaires, telles que les publicités superposées, les publicités compagnons dynamiques, les publicités minimalisables, les publicités réductibles et les publicités extensibles.
* Préchargement des publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID Flash

## API {#section_0DB1D383CA5047B281BC808BC082C69B}

Les éléments d’API suivants prennent en charge les publicités VPAID 2.0 :

* La variable `getCustomAdView` méthode de `MediaPlayer` renvoie une `CustomAdView` qui représente l’affichage web qui effectue le rendu de la publicité VPAID.

  Pour plus d’informations sur la variable `getCustomAdView` , voir [Documentation de l’API MediaPlayer](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.MediaPlayer.html).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` définit le délai d’expiration sur le processus de chargement VPAID.

  La valeur par défaut du délai d’expiration est de 10 secondes.

* L&#39;API, `auditudeSettings.ignoreVPAIDAds`, vous permet d’ignorer les publicités VPAID reçues du serveur Auditude. L’API ne fonctionne pas pour le Flash de secours.

Pendant la lecture de la publicité VPAID :

* La publicité VPAID s’affiche dans un conteneur d’affichage au-dessus de la vue du lecteur, de sorte que le code qui repose sur les clics des utilisateurs sur la vue du lecteur ne fonctionne pas.
* Les appels à la mise en pause et à la lecture sur l’instance du lecteur s’arrêtent et reprennent la publicité VPAID.
* Les publicités VPAID n’ont pas de durée prédéfinie, car elles peuvent être interactives.

  La durée de la publicité et la durée totale de coupure publicitaire spécifiées dans la réponse du serveur de publicités peuvent ne pas être exactes.
