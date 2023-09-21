---
description: Pour afficher les bannières publicitaires, vous devez créer des instances de bannière et permettre à TVSDK d’écouter les événements liés aux publicités.
title: Afficher les bannières publicitaires
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher les bannières publicitaires, vous devez créer des instances de bannière et permettre à TVSDK d’écouter les événements liés aux publicités.

TVSDK fournit une liste des bannières publicitaires associées à une publicité linéaire par le biais de la variable `AdPlaybackEventListener.onAdBreakStart` .

Les manifestes peuvent spécifier des bannières publicitaires d’accompagnement en :

* Fragment de HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier de SWF de Flash Adobe

Pour chaque publicité compagnon, TVSDK indique les types disponibles pour votre application.

1. Ajoutez un écouteur pour la fonction `AdPlaybackEventListener.onAdBreakStart` qui effectue les opérations suivantes :

   * Efface les publicités existantes dans l’instance de bannière.
   * Récupère la liste des publicités compagnons à partir de `Ad.getCompanionAssets`.
   * Si la liste des publicités d’accompagnement n’est pas vide, passez la souris sur la liste pour les instances de bannière.

     Chaque instance de bannière (une `AdAsset`) contient des informations, telles que la largeur, la hauteur, le type de ressource (html, iframe ou statique), ainsi que les données requises pour afficher la bannière compagnon.
   * Si une publicité vidéo ne comporte aucune publicité compagnon enregistrée, la liste des ressources compagnons ne contient aucune donnée pour cette publicité vidéo.
   * Pour afficher une publicité d’affichage autonome, ajoutez la logique à votre script afin d’exécuter une balise d’affichage publicitaire standard DFP (DoubleClick for Publishers) dans l’instance de bannière appropriée.
   * Envoie les informations sur la bannière à une fonction de votre page qui affiche les bannières à un emplacement approprié.

     Il s’agit généralement d’une `div`, et votre fonction utilise la fonction `div ID` pour afficher la bannière.
