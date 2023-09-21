---
title: Mise en cache
description: Mise en cache
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Mise en cache HTTP {#caching}

Par défaut, l’Ad Insertion Primetime respecte les en-têtes de contrôle du cache HTTP lors de la récupération des éléments créatifs publicitaires ainsi que du contenu.  Cela peut réduire considérablement le nombre de requêtes réseau requises par l’Ad Insertion Primetime pour envoyer le réseau de diffusion de contenu à tous les clients.  Pour la mise en cache, Adobe recommande les paramètres suivants et implique l’envoi de l’en-tête HTTP `max-age` de votre réseau de diffusion de contenu.  Contactez votre représentant du réseau de diffusion de contenu pour activer ces en-têtes sur vos diffusions vidéo et vos diffusions publicitaires.

## Pour le contenu en direct/linéaire {#caching-live-linear-content}

* Manifeste de Principal : 24 heures, ou Cache-Control: max-age=86400
* Manifeste multimédia : 1 seconde ou Cache-Control: max-age=1

## Pour le contenu VOD {#caching-vod-content}

* Manifeste de Principal : 24 heures, ou Cache-Control: max-age=86400
* Manifeste multimédia : 24 heures, ou Cache-Control: max-age=86400
