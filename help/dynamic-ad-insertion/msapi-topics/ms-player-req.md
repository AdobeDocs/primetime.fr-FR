---
description: Tous les lecteurs vidéo doivent fournir des fonctionnalités sur lesquelles le serveur de manifeste se base pour insérer des publicités et activer le suivi des publicités.
seo-description: Tous les lecteurs vidéo doivent fournir des fonctionnalités sur lesquelles le serveur de manifeste se base pour insérer des publicités et activer le suivi des publicités.
seo-title: Configuration requise pour le lecteur vidéo
title: Configuration requise pour le lecteur vidéo
uuid: 29593d67-2901-4d9e-a08f-23c8a7667283
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Configuration requise pour le lecteur vidéo {#video-player-requirements}

Tous les lecteurs vidéo doivent fournir des fonctionnalités sur lesquelles le serveur de manifeste se base pour insérer des publicités et activer le suivi des publicités.

Pour utiliser l’API Primetime et d’insertion, un lecteur vidéo doit répondre aux critères suivants :

* Peut effectuer le suivi de la position du curseur de lecture lorsque le contenu est lu.
* Peut demander des URL de suivi aux moments spécifiés.
* S’exécute sur une plate-forme de périphérique prenant en charge HLS v3 ou version ultérieure, notamment :

   * Discontinuations PTS marquées par des `EXT-X-DISCONTINUITY` balises
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* S’exécute sur une plateforme qui prend en charge les redirections HTTP et l’analyse de JSON.
* S’exécute sur une plateforme prenant en charge CORS.