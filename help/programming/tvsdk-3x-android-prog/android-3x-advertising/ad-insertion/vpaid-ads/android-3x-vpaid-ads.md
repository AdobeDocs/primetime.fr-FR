---
description: La version 2.0 de l’interface de définition de l’interface de diffusion d’annonces du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.
seo-description: La version 2.0 de l’interface de définition de l’interface de diffusion d’annonces du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.
seo-title: Prise en charge des publicités VPAID 2.0
title: Prise en charge des publicités VPAID 2.0
uuid: e45e91d2-2aef-4d69-ac80-228d23e8fd7b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Aperçu {#vpaid-ad-support-overview}

La version 2.0 de l’interface de définition de l’interface de diffusion d’annonces du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. Il offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.

Les fonctionnalités suivantes sont prises en charge :

* Version 2.0 de la spécification VPAID

   Pour plus d&#39;informations, consultez [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Publicités VPAID linéaires avec contenu vidéo à la demande (VOD)
* Publicités VPAID JavaScript

   Les publicités VPAID doivent être basées sur JavaScript et la réponse publicitaire doit identifier le type de média de la publicité VPAID comme `application/javascript`.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Version 1.0 de la spécification VPAID
* Annonces ignorées
* Publicités non linéaires, telles que publicités d’incrustation, publicités compagnons dynamiques, publicités pouvant être réduites, publicités réductibles et annonces extensibles
* Prévisualisation de publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID Flash

## API

Les éléments d&#39;API suivants prennent en charge les annonces VPAID 2.0 :

* La méthode `getCustomAdView` de `MediaPlayer` renvoie un objet `CustomAdView` représentant la vue Web qui effectue le rendu de la publicité VPAID (voir [Références API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html)).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` définit le délai d’expiration sur le processus de chargement VPAID. Le délai d’expiration par défaut est de 10 secondes.

Pendant la lecture de la publicité VPAID :

* La publicité VPAID est affichée dans un conteneur de vue au-dessus de la vue du lecteur. Par conséquent, le code qui repose sur les clics effectués par les utilisateurs sur la vue du lecteur ne fonctionne pas.
* Les appels à `pause` et `play` sur l’instance du lecteur s’interrompent et reprennent la publicité VPAID.

* Les publicités VPAID n’ont pas de durée prédéfinie, car elles peuvent être interactives.

   La durée de la publicité et la durée totale de la coupure publicitaire spécifiées dans la réponse du serveur publicitaire peuvent ne pas être exactes.