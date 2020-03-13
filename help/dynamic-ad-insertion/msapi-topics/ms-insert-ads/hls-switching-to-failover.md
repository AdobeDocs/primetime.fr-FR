---
description: La pile HLS d’Apple prend en charge le passage aux flux de basculement/sauvegarde s’il ne parvient pas à récupérer les flux du jeu principal. Pour les périphériques Apple HLS, pour faciliter le basculement, vous pouvez signaler au serveur manifest de traiter les flux principaux et de basculement identifiés dans la liste de lecture principale comme des jeux disjoints (avec leurs propres UUID).
seo-description: La pile HLS d’Apple prend en charge le passage aux flux de basculement/sauvegarde s’il ne parvient pas à récupérer les flux du jeu principal. Pour les périphériques Apple HLS, pour faciliter le basculement, vous pouvez signaler au serveur manifest de traiter les flux principaux et de basculement identifiés dans la liste de lecture principale comme des jeux disjoints (avec leurs propres UUID).
seo-title: Faciliter le passage du lecteur HLS aux flux de basculement/sauvegarde
title: Faciliter le passage du lecteur HLS aux flux de basculement/sauvegarde
uuid: 2fea8a51-e4cb-4fc9-82d5-6305a1d96603
translation-type: tm+mt
source-git-commit: 6863b63c7fa0068c3c5060fb946515c6cc5e3bff

---


# Faciliter le passage du lecteur HLS aux flux de basculement/sauvegarde {#facilitating-hls-player-switching-to-failover-backup-streams}

La pile HLS d’Apple prend en charge le passage aux flux de basculement/sauvegarde s’il ne parvient pas à récupérer les flux du jeu principal. Pour les périphériques Apple HLS, pour faciliter le basculement, vous pouvez signaler au serveur manifest de traiter les flux principaux et de basculement identifiés dans la liste de lecture principale comme des jeux disjoints (avec leurs propres UUID).

Pour faciliter le basculement vers les flux de basculement ou de sauvegarde sur les périphériques Apple HLS, vous pouvez spécifier le `ptfailover` paramètre dans l’URL d’amorçage. Si vous fournissez ce paramètre, le serveur de manifeste crée des sessions de lecture distinctes (qui déterminent les publicités assemblées) pour chaque jeu de basculement.

## Détails

Comment SSAI gère le basculement HLS vers basculement/sauvegarde lorsque vous incluez `ptfailover=true` dans la demande d’amorçage :

* Lorsqu’une liste de lecture principale contient des jeux principaux et de sauvegarde :

   * Le serveur de manifeste identifie les URL de flux AV pour différents jeux de basculement à l’aide de l’ `BANDWIDTH` attribut et de l’ordre d’analyse des URL de flux AV. Il crée des sessions de lecture internes distinctes (identifiées par des UUID distincts) et crée des URL de diffusion en continu pointant vers des serveurs de manifeste avec les différents UUID identifiant les différentes sessions de lecture.
   * Le serveur de manifeste identifie les URL de flux d’I-Frame pour différents jeux de basculement à l’aide de l’ `RESOLUTION` attribut correspondant et de l’ordre d’analyse des URL de flux d’I-Frame. SSAI utilise les UUID identifiant les flux AV associés pour les URL de flux d’I-Frame pointant vers SSAI.
   * Pour cette fonctionnalité, le serveur de manifeste ne prend en charge que `EXT-X-MEDIA` les groupes sans attributs URI dans la liste de lecture principale.
   * Le serveur de manifeste détecte une réponse d’erreur 404 d’un CDN avec un `X-Object-Too-Old: true` en-tête et conserve le code d’état et l’en-tête lors de l’envoi de cette réponse au lecteur.

* Les publicités preroll ne sont ajoutées qu’au jeu principal ; elles sont complètement désactivées dans les jeux de basculement afin d’éviter toute publicité preroll erronée et/ou dupliquée lorsque le lecteur bascule sur des flux de basculement.

