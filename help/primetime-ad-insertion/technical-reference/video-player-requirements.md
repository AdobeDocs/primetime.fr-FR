---
description: Tous les lecteurs vidéo doivent fournir des fonctionnalités sur lesquelles le serveur de manifeste utilise pour insérer des publicités et activer le suivi des publicités.
seo-description: Tous les lecteurs vidéo doivent fournir des fonctionnalités sur lesquelles le serveur de manifeste utilise pour insérer des publicités et activer le suivi des publicités.
seo-title: Configuration requise pour le lecteur vidéo
title: Configuration requise pour le lecteur vidéo
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# Configuration requise pour le lecteur vidéo {#video-player-requirements}

Tous les lecteurs vidéo doivent fournir des fonctionnalités sur lesquelles le serveur de manifeste utilise pour insérer des publicités et activer le suivi des publicités.

Pour utiliser l’API d’insertion et Primetime, un lecteur vidéo doit satisfaire aux exigences suivantes :

* Peut effectuer le suivi de la position du curseur de lecture au fur et à mesure de la lecture du contenu.
* Peut demander des URL de suivi aux moments spécifiés.
* S’exécute sur une plate-forme de périphérique qui prend en charge HLS v3 ou version ultérieure, notamment :

   * Discontinuations PTS marquées par des balises `EXT-X-DISCONTINUITY`
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* S’exécute sur une plateforme qui prend en charge les redirections HTTP et l’analyse de JSON.
* Les lecteurs Web doivent s’exécuter sur des plateformes prenant en charge CORS.