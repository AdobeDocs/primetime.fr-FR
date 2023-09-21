---
description: La pile HLS Apple prend en charge le basculement/sauvegarde des flux s’il ne parvient pas à récupérer les flux de l’ensemble principal. Pour les appareils HLS Apple, afin de faciliter le basculement, vous pouvez signaler au serveur manifeste qu’il traite les diffusions principales et de basculement identifiées dans la liste de lecture principale comme des visionneuses disjointes (avec leurs propres UUID).
title: Faciliter le passage du lecteur HLS aux diffusions de basculement/sauvegarde
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# Faciliter le passage du lecteur HLS aux diffusions de basculement/sauvegarde {#facilitating-hls-player-switching-to-failover-backup-streams}

La pile HLS Apple prend en charge le basculement/sauvegarde des flux s’il ne parvient pas à récupérer les flux de l’ensemble principal. Pour les appareils HLS Apple, afin de faciliter le basculement, vous pouvez signaler au serveur manifeste qu’il traite les diffusions principales et de basculement identifiées dans la liste de lecture principale comme des visionneuses disjointes (avec leurs propres UUID).

Pour faciliter le basculement vers des diffusions de sauvegarde ou de basculement sur des appareils HLS Apple, vous pouvez spécifier la variable `ptfailover` dans l’URL du Bootstrap. Si vous fournissez ce paramètre, le serveur de manifeste crée des sessions de lecture distinctes (qui déterminent les publicités regroupées) pour chaque jeu de basculement.

## Détails

Comment SSAI gère le basculement/sauvegarde HLS lorsque vous incluez `ptfailover=true` dans la requête du Bootstrap :

* Lorsqu’une liste de lecture principale contient des ensembles principal et de sauvegarde :

   * Le serveur de manifeste identifie les URL de diffusion A/V pour différents jeux de basculement à l’aide de la variable `BANDWIDTH` et l’ordre d’analyse des URL de diffusion A/V. Il crée des sessions de lecture internes distinctes (identifiées par des UUID distincts) et crée des URL de diffusion pointant vers des serveurs de manifeste avec les différents UUID identifiant différentes sessions de lecture.
   * Le serveur de manifeste identifie les URL de flux d’I-Frame pour différents jeux de basculement à l’aide de la correspondance `RESOLUTION` et l’ordre d’analyse des URL de diffusion en continu d’images. SSAI utilise les UUID qui identifient les flux AV associés pour les URL de diffusion I-Frame pointant vers SSAI.
   * Pour cette fonctionnalité, le serveur de manifeste ne prend en charge que `EXT-X-MEDIA` groupes sans attributs URI dans la liste de lecture principale.
   * Le serveur de manifeste détecte une réponse d’erreur 404 d’un CDN avec une `X-Object-Too-Old: true` et conserve le code d’état et l’en-tête lors de l’envoi de cette réponse au lecteur.

* Les publicités preroll ne sont ajoutées qu’à l’ensemble principal ; elles sont complètement désactivées dans les jeux de basculement afin d’éviter toute publicité preroll erronée et/ou dupliquée lorsque le lecteur passe en flux de basculement.

