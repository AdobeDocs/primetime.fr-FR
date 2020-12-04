---
description: La pile HLS d’Apple prend en charge le basculement vers les flux de basculement/sauvegarde s’il ne parvient pas à récupérer les flux du jeu Principal. Pour les périphériques Apple HLS, pour faciliter le basculement, vous pouvez signaler au serveur manifest de traiter les flux Principaux et de basculement identifiés dans la liste de lecture principale comme des jeux disjoints (avec leurs propres UUID).
seo-description: La pile HLS d’Apple prend en charge le basculement vers les flux de basculement/sauvegarde s’il ne parvient pas à récupérer les flux du jeu Principal. Pour les périphériques Apple HLS, pour faciliter le basculement, vous pouvez signaler au serveur manifest de traiter les flux Principaux et de basculement identifiés dans la liste de lecture principale comme des jeux disjoints (avec leurs propres UUID).
seo-title: Faciliter le passage du lecteur HLS aux flux de basculement/sauvegarde
title: Faciliter le passage du lecteur HLS aux flux de basculement/sauvegarde
uuid: 2fea8a51-e4cb-4fc9-82d5-6305a1d96603
translation-type: tm+mt
source-git-commit: 6863b63c7fa0068c3c5060fb946515c6cc5e3bff
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Faciliter le passage du lecteur HLS aux flux de basculement/sauvegarde {#facilitating-hls-player-switching-to-failover-backup-streams}

La pile HLS d’Apple prend en charge le basculement vers les flux de basculement/sauvegarde s’il ne parvient pas à récupérer les flux du jeu Principal. Pour les périphériques Apple HLS, pour faciliter le basculement, vous pouvez signaler au serveur manifest de traiter les flux Principaux et de basculement identifiés dans la liste de lecture principale comme des jeux disjoints (avec leurs propres UUID).

Pour faciliter le basculement sur incident ou les flux de sauvegarde sur les périphériques Apple HLS, vous pouvez spécifier le paramètre `ptfailover` dans l’URL du Bootstrap. Si vous fournissez ce paramètre, le serveur de manifeste crée des sessions de lecture distinctes (qui déterminent les publicités assemblées) pour chaque jeu de basculement.

## Détails

Comment SSAI gère le basculement HLS sur basculement/sauvegarde lorsque vous incluez `ptfailover=true` dans la demande du Bootstrap :

* Lorsqu’une liste de lecture principale contient des visionneuses Principales et de sauvegarde :

   * Le serveur de manifeste identifie les URL de flux AV pour différents jeux de basculement à l’aide de l’attribut `BANDWIDTH` et de l’ordre d’analyse des URL de flux AV. Il crée des sessions de lecture internes distinctes (identifiées par des UUID distincts) et crée des URL de diffusion en continu pointant vers des serveurs de manifeste dont les différents UUID identifient différentes sessions de lecture.
   * Le serveur de manifeste identifie les URL de flux d’I-Frame pour différents jeux de basculement à l’aide de l’attribut `RESOLUTION` correspondant et de l’ordre d’analyse des URL de flux d’I-Frame. SSAI utilise les UUID qui identifient les flux AV associés pour les URL de flux d’E-Frame pointant vers SSAI.
   * Pour cette fonctionnalité, le serveur de manifeste ne prend en charge que les groupes `EXT-X-MEDIA` sans attributs URI dans la liste de lecture principale.
   * Le serveur de manifeste détecte une réponse d&#39;erreur 404 d&#39;un CDN avec un en-tête `X-Object-Too-Old: true` et conserve le code d&#39;état et l&#39;en-tête lors de l&#39;envoi de cette réponse au lecteur.

* Les publicités preroll ne sont ajoutées qu’au jeu Principal ; elles sont complètement désactivées dans les jeux de basculement afin d’éviter toute publicité preroll erronée et/ou dupliquée lorsque le lecteur bascule sur des flux de basculement.

