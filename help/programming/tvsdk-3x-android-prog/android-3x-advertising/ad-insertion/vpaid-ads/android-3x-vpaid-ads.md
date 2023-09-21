---
description: La définition de l’interface de service publicitaire du lecteur vidéo (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre une expérience multimédia riche aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
title: Prise en charge des publicités VPAID 2.0
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Présentation {#vpaid-ad-support-overview}

La définition de l’interface de service publicitaire du lecteur vidéo (VPAID) 2.0 fournit une interface commune pour lire des publicités vidéo. Il offre une expérience multimédia riche aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.

Les fonctionnalités suivantes sont prises en charge :

* Version 2.0 de la spécification VPAID

  Pour plus d’informations, voir [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Publicités VPAID linéaires avec contenu vidéo à la demande (VOD)
* Publicités JavaScript VPAID

  Les publicités VPAID doivent être basées sur JavaScript et la réponse publicitaire doit identifier le type de média de la publicité VPAID comme `application/javascript`.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Version 1.0 de la spécification VPAID
* Publicités ignorables
* Publicités non linéaires, telles que les publicités superposées, les publicités compagnons dynamiques, les publicités minimalisables, les publicités réductibles et les publicités extensibles
* Préchargement des publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID Flash

## API

Les éléments d’API suivants prennent en charge les publicités VPAID 2.0 :

* La variable `getCustomAdView` méthode de `MediaPlayer` renvoie une `CustomAdView` , représentant l’affichage web qui effectue le rendu de la publicité VPAID (voir [Références API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html)).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` définit le délai d’expiration sur le processus de chargement VPAID. La valeur par défaut du délai d’expiration est de 10 secondes.

Pendant la lecture de la publicité VPAID :

* La publicité VPAID s’affiche dans un conteneur d’affichage au-dessus de la vue du lecteur, de sorte que le code qui repose sur les clics des utilisateurs sur la vue du lecteur ne fonctionne pas.
* Appels à `pause` et `play` sur l’instance du lecteur, arrêtez-la et reprenez la publicité VPAID.

* Les publicités VPAID n’ont pas de durée prédéfinie, car elles peuvent être interactives.

  La durée de la publicité et la durée totale de coupure publicitaire spécifiées dans la réponse du serveur de publicités peuvent ne pas être exactes.
