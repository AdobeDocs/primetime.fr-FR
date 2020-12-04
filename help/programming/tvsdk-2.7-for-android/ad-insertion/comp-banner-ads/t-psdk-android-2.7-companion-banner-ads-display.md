---
description: Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser TVSDK à écouter les événements liés aux publicités.
seo-description: Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser TVSDK à écouter les événements liés aux publicités.
seo-title: Afficher les bannières publicitaires
title: Afficher les bannières publicitaires
uuid: 7246dfab-860f-4b55-9554-49738a483406
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser TVSDK à écouter les événements liés aux publicités.

TVSDK fournit une liste de bannières publicitaires associées associées à une publicité linéaire via le événement `AdPlaybackEventListener.onAdBreakStart`.

Les manifestes peuvent spécifier des bannières publicitaires complémentaires en :

* Un extrait de code HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier SWF de Flash d’Adobe

Pour chaque publicité connexe, TVSDK indique les types disponibles pour votre application.

1. Ajoutez un écouteur pour le événement `AdPlaybackEventListener.onAdBreakStart` qui effectue les opérations suivantes :

   * Efface les publicités existantes dans l’instance de bannière.
   * Obtient la liste des publicités complémentaires de `Ad.getCompanionAssets`.
   * Si la liste des publicités complémentaires n’est pas vide, effectuez une itération sur la liste pour les instances de bannière.

      Chaque instance de bannière (une `AdAsset`) contient des informations telles que la largeur, la hauteur, le type de ressource (html, iframe ou static) et les données requises pour afficher la bannière correspondante.
   * Si une publicité vidéo ne comporte aucune publicité connexe, la liste des ressources d’accompagnement ne contient aucune donnée pour cette publicité vidéo.
   * Pour afficher une publicité d’affichage autonome, ajoutez la logique à votre script afin d’exécuter une balise d’affichage publicitaire standard DFP (DoubleClick for Publishers) dans l’instance de bannière appropriée.
   * Envoie les informations de la bannière à une fonction de votre page qui affiche les bannières à l’emplacement approprié.

      Il s&#39;agit généralement d&#39;un `div` et votre fonction utilise le `div ID` pour afficher la bannière.

