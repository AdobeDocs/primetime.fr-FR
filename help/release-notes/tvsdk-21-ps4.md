---
title: Notes de mise à jour de TVSDK 2.1 PlayStation 4
seo-title: Notes de mise à jour de TVSDK 2.1 PlayStation 4
description: Les Notes de mise à jour de TVSDK 2.1 pour PlayStation 4 décrivent les fonctionnalités prises en charge et les problèmes connus de TVSDK 2.1 PlayStation 4 .
seo-description: Les Notes de mise à jour de TVSDK 2.1 pour PlayStation 4 décrivent les fonctionnalités prises en charge et les problèmes connus de TVSDK 2.1 PlayStation 4 .
uuid: 494569cf-07e2-476a-b88e-e46c9cca4cdc
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: ebfc8819-f5a9-47a2-b454-0e4e6f9e4640
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Notes de mise à jour de TVSDK 2.1 PlayStation 4 {#tvsdk-playstation-release-notes}

Les Notes de mise à jour de TVSDK 2.1 pour PlayStation 4 décrivent les fonctionnalités prises en charge et les problèmes connus de TVSDK 2.1 PlayStation 4 .

## Problèmes résolus {#resolved-issues}

Voici les problèmes résolus pour TVSDK 2.1 pour PlayStation 4 :

**Version 2.1.0.638**

* **PTPLAY-10439 :**
Lorsque le lien publicitaire d’enveloppe VMAP était rompu, le lecteur se retrouvait bloqué dans l’état de préparation (il n’était pas envoyé `onComplete` à son appelant).

* **PTPLAY-10179 :**
   `creativeRepackaging` et `fallbackOnInvalidCreative` les valeurs sont désormais désactivées par défaut. En outre, lorsque l’ `creativeRepackaging` indicateur était défini mais qu’aucun `creativeRepackaging` format n’était fourni, l’ `onRepackagingComplete` utilisateur était appelé autant de fois que des publicités étaient présentes dans la coupure publicitaire, ce qui entraînait la création de pauses publicitaires à plusieurs reprises.

* **Zendesk #10304**:
La variable d&#39;annulation de publicité n&#39;a pas été initialisée. Nous initialisons désormais la variable à partir de `DataSetEntry's` ctor.

* **PTPLAY-10318 :**
Le mode arrière-plan a été pris en charge.
* **Zendesk n° 17409 :**
Lorsque vous passez en mode de lecture par astuce, puis revenez en mode de lecture normal, puis de nouveau en mode de lecture par astuce, la position de lecture était en train de sauter.
* **PTPLAY-9552 :**
Après l’analyse des fichiers XML de réponse, le code d’erreur 1108 est maintenant épinglé chaque fois qu’il n’y a aucune publicité.
* **PTPLAY-9551 :**
S’il n’y a pas de coupure publicitaire après le traitement d’Auditude, le CRS appelle **onPrefetchComplete** qui décrémente le groupCount. Puisqu’il n’y a pas de coupure publicitaire, le **groupeCount** est égal à 0 et décrété par 1. Auparavant, **groupCount** était **uint32_t** car il était utilisé pour passer à la valeur maximale. C&#39;est maintenant **int32_t**.

**Version 2.1.0.621**

* **Zendesk #4555** Instant on Memory (Problèmes de mémoire générant des erreurs de chargement) - `MediaItemLoader` Correctif du plantage lors de la libération `mediaitemloader`

* **Zendesk #17223** 2.x CSAI: Toutes les URL de suivi des publicités ne se déclenchent pas
   * Certaines publicités VAST pointant ensuite vers une publicité intégrée manquaient d’URL de suivi.
   * Lorsque plusieurs balises d’impression se trouvent dans une publicité au format XML VAST, seule la première URL d’impression a été enregistrée et le reste a été ignoré. Désormais, toutes les URL d’impression seront enregistrées et épinglées ultérieurement.
* **Zendesk #17224** PS4 L’agent utilisateur déplace les informations d’heure de début à la fin de la chaîne UAString
* **Zendesk #17226** 2.x CSAI: Toutes les publicités ne sont pas collées.\
   Le correctif consiste à indiquer que le plan de montage chronologique a changé en raison des opérations insertBy ou eraseBy et à effectuer le changement de point en conséquence.

* **Zendesk #17284**
   [Toutes les plateformes] Les sous-titres codés ne s’affichent pas.\
   HLS : prise en charge de la `EXT-X-MEDIA-TIME` balise pour les fichiers de sous-titrage VTT.

* **Zendesk #17889** Lecture &quot;Lactée&quot; sur PS4\
   décalage correct appliqué (pour la conversion des couleurs)

* **Zendesk #17954** Logique de secours de publicité + gestion de l&#39;étendue vide\
   Correction d’un problème en raison duquel l’un des wrappers Vast était vide, l’analyseur Vast continuait à traiter le wrapper.

* **Zendesk #17807** Ne peut pas dépasser vaste videIdentique à Zendesk #3103

* **Zendesk #17865** Logique de secours sur PS4 et XBox One\
   Identique à Zendesk #3103

**Version 2.1.0.591**

* **Code d’annonce Zendesk #3767** PS4, la résolution de publicité échoue lors du traitement des redirections VMAP.
* **Zendesk #4096** PS4 CSAI : Défaut de segmentationCorrection d’un blocage lorsque TVSDK renvoie une erreur de segmentation lorsque la bibliothèque publicitaire traite une réponse VMAP.

* **Zendesk #4161** Trickplay 16x à la fin du film se bloqueCorrection d’un blocage survenant lorsque le trickplay revient à la lecture normale

* **Zendesk #4208** Blocage aléatoire lorsque les sous-titres sont activésBlocage de mémoire fixe lorsque les sous-titres sont activés

* **Zendesk #4213** PS4 CSAI : Modifier la chaîne user-agent par défaut pour tous les appels liés à la publicitéLa chaîne user-agent est créée à l’aide de la même chaîne UA que celle utilisée par le navigateur + ajouter une chaîne Primetime

* **PTPLAY-7675** (interne) Les publicités transcodées ne sont pas luesCreative Repackaging échouait lorsqu’il était appelé dans une réponse VMAP ou VAST. Le correctif consiste à simplement lire le fichier média à partir de la publicité au lieu de lire à partir de la ressource dans le cas de grandes publicités.

* **PTPLAY-7895** (interne)Lorsque `allowMultipleAds=false`, aucune publicité n&#39;est lueCorrection d&#39;un bogue quand `allowMultipleAds` le paramètre n&#39;était pas correctement suivi.

* **PTPLAY-7896** (interne) Les publicités s’exécutent en séquence sur PS4Correction d’un problème en raison duquel les publicités n’étaient pas dans l’ordre dans lequel elles apparaissaient dans les réponses XML.

* PS4 TVSDK a été testé dans une mini-application plutôt que dans un jeu.

**Version 2.1.0.563**

* **Zendesk #3868** Le SDK TVSDK prend-il en charge le SDK Playstation 2.5 Le SDK TVSDK est maintenant créé avec le SDK Playstation 2.5.

* **Zendesk #4093** targetingInfo paires clé-valeur dans la demande Publicités Pt.\
   Un caractère de nouvelle ligne séparant les paires clé/valeur a été ajouté.

## Fonctionnalités prises en charge {#supported-features}

Les fonctionnalités suivantes sont prises en charge dans TVSDK 2.1 pour PlayStation 4 :

**Version 2.1.0.621**

* Abandon de publicité, chaînement de publicités dans la logique de sélection de publicités (Zendesk #3103) Pour les publicités VAST (créatifs) avec la règle de secours activée, le TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d&#39;utiliser des publicités de secours à sa place.Vous pouvez configurer certains aspects du comportement de secours

**Version 2.1.0.538**

* Lecture VOD HLS, y compris lecture, pause, recherche
* Diffusion en flux continu adaptatif
* Lecture de contenu chiffré avec le contenu protégé par DRM Primetime et AES vanille
* Insertion de publicité côté client avec comportements publicitaires par défaut et annulation de publicité
* Reconditionnement créatif
* Sous-titres WebVTT
* Installez-le avec la position  du personnalisé
* Jouer à la vitesse supérieure et au retour rapide
* 302 redirection

## Ressources utiles {#helpful-resources}

* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.