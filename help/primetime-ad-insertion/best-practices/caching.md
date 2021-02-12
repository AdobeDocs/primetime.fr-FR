---
title: Mise en cache
description: null
translation-type: tm+mt
source-git-commit: 76dc54fabdae400ad708ba83fcf6f7fd5caa2b22
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# Mise en cache HTTP {#caching}

Par défaut, l’Ad Insertion Primetime respecte les en-têtes de contrôle du cache HTTP lors de la récupération des éléments créatifs publicitaires ainsi que du contenu.  Cela peut réduire considérablement le nombre de demandes réseau que l’Ad Insertion Primetime doit effectuer sur le réseau de diffusion de contenu pour tous les clients.  Pour la mise en cache, l’Adobe recommande les paramètres suivants et implique l’envoi de l’en-tête HTTP `max-age` à partir du CDN.  Contactez votre représentant CDN pour activer ces en-têtes dans vos flux vidéo et publicitaires.

## Pour le contenu en direct/linéaire {#caching-live-linear-content}

* Manifeste de Principal : 24 heures, ou Cache-Control : max-age=86 400
* Manifeste multimédia : 1 seconde, ou Cache-Control : max-age=1

## Pour le contenu VOD {#caching-vod-content}

* Manifeste de Principal : 24 heures, ou Cache-Control : max-age=86 400
* Manifeste multimédia : 24 heures, ou Cache-Control : max-age=86 400
