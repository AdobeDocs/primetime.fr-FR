---
description: Tous les lecteurs vidéo doivent fournir des fonctionnalités sur lesquelles le serveur de manifeste repose pour insérer des publicités et activer le suivi des publicités.
title: Exigences relatives au lecteur vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Exigences relatives au lecteur vidéo {#video-player-requirements}

Tous les lecteurs vidéo doivent fournir des fonctionnalités sur lesquelles le serveur de manifeste repose pour insérer des publicités et activer le suivi des publicités.

Pour utiliser l’API d’insertion de publicités Primetime, un lecteur vidéo doit répondre aux exigences suivantes :

* Peut effectuer le suivi de la position du curseur de lecture au fur et à mesure de la lecture du contenu.
* Peuvent demander des URL de suivi aux moments spécifiés.
* S’exécute sur une plate-forme d’appareil qui prend en charge HLS v3 ou version ultérieure, notamment :

   * Les discontinuations PTS marquées par `EXT-X-DISCONTINUITY` tags
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* S’exécute sur une plateforme qui prend en charge les redirections HTTP et l’analyse JSON.
* Les lecteurs Web doivent s’exécuter sur des plateformes qui prennent en charge CORS.
