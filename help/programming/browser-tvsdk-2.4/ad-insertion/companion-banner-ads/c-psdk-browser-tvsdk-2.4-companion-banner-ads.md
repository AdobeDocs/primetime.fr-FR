---
description: Le TVSDK du navigateur prend en charge les bannières publicitaires compagnons, qui sont des publicités qui accompagnent une publicité linéaire et restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l’affichage des bannières compagnons fournies avec une publicité linéaire.
title: Bannières publicitaires d’accompagnement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Présentation {#companion-banner-ads-overview}

Le TVSDK du navigateur prend en charge les bannières publicitaires compagnons, qui sont des publicités qui accompagnent une publicité linéaire et restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l’affichage des bannières compagnons fournies avec une publicité linéaire.

Lors de l’affichage des publicités compagnons, procédez comme suit :

* Essayez de présenter autant de bannières publicitaires d’accompagnement que vous le souhaitez dans la disposition de votre lecteur.
* Présenter une bannière compagnon uniquement si vous disposez d’un emplacement correspondant à la hauteur et à la largeur spécifiées de la bannière compagnon.

  >[!TIP]
  >
  >Ne redimensionnez pas la bannière.

* Présenter la ou les bannières d’accompagnement dès que possible après le début de la publicité.
* Ne superposez pas le conteneur publicitaire/vidéo principal avec les bannières compagnons.
* Continuez à afficher les bannières compagnons une fois la publicité terminée.

  La norme consiste à afficher chaque bannière compagnon jusqu’à ce que vous ayez un remplacement pour cette bannière.
