---
description: Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser TVSDK à écouter les  liées aux publicités.
seo-description: Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser TVSDK à écouter les  liées aux publicités.
seo-title: Afficher les bannières publicitaires
title: Afficher les bannières publicitaires
uuid: cfd4b26c-9643-4b60-9aff-bc27dec289f1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser TVSDK à écouter les  liées aux publicités.

TVSDK fournit un de bannières publicitaires associées associées à une publicité linéaire par l’intermédiaire de l’ `AdPlaybackEventListener.onAdBreakStart` .

Les manifestes peuvent spécifier des bannières publicitaires d&#39;accompagnement par :

* Un extrait de code HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier SWF Adobe Flash

Pour chaque publicité connexe, TVSDK indique les types disponibles pour votre application.

1. Ajouter un écouteur pour le `AdPlaybackEventListener.onAdBreakStart` qui effectue les actions suivantes :

   * Efface les publicités existantes dans l’instance de bannière.
   * Obtient le  des publicités d&#39;accompagnement `Ad.getCompanionAssets`.
   * Si le  des publicités complémentaires n’est pas vide, effectuez une itération sur le pour les instances de bannière.

      Chaque instance de bannière (une `AdAsset`) contient des informations, telles que la largeur, la hauteur, le type de ressource (html, iframe ou statique), ainsi que les données requises pour afficher la bannière correspondante.
   * Si une publicité vidéo ne comporte aucune publicité connexe, le  des ressources connexes ne contient aucune donnée pour cette publicité vidéo.
   * Pour afficher une publicité d’affichage autonome, ajoutez la logique à votre script afin d’exécuter une balise d’affichage publicitaire d’affichage DFP normale (DoubleClick for Publishers) dans l’instance de bannière appropriée.
   * Envoie les informations sur la bannière à une fonction de votre page qui affiche les bannières à l’emplacement approprié.

      Il s’agit généralement d’une `div`, et votre fonction utilise la `div ID` pour afficher la bannière.