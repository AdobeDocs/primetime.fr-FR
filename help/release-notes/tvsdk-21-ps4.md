---
title: Notes de mise à jour de TVSDK 2.1 PlayStation 4
description: Les notes de mise à jour de TVSDK 2.1 pour PlayStation 4 décrivent les fonctionnalités prises en charge et les problèmes connus de TVSDK 2.1 PlayStation 4 .
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
exl-id: 32af3fe4-c730-41f6-a558-987bd14c9bae
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Notes de mise à jour de TVSDK 2.1 PlayStation 4 {#tvsdk-playstation-release-notes}

Les notes de mise à jour de TVSDK 2.1 pour PlayStation 4 décrivent les fonctionnalités prises en charge et les problèmes connus de TVSDK 2.1 PlayStation 4 .

## Problèmes résolus {#resolved-issues}

Voici les problèmes résolus pour TVSDK 2.1 pour PlayStation 4 :

**Version 2.1.0.638**

* **PTPLAY-10439 :**
Lorsque le lien de publicité de l’élément wrapper VMAP était rompu, le lecteur était bloqué à l’état Préparation (il n’envoyait pas). 
`onComplete` à son appelant).

* **PTPLAY-10179 :**

   `creativeRepackaging` et `fallbackOnInvalidCreative` sont désormais désactivées par défaut. En outre, lorsque la variable `creativeRepackaging` L’indicateur a été défini mais aucun `creativeRepackaging` Le format a été fourni, la valeur `onRepackagingComplete` était appelé autant de fois que des publicités étaient présentes dans la coupure publicitaire, ce qui provoquait la création de coupures publicitaires à plusieurs reprises.

* **Zendesk #10304**: La variable d’annulation de la publicité n’a pas été initialisée. Nous initialisons désormais la variable à partir de `DataSetEntry's` ctor.

* **PTPLAY-10318 :**
La prise en charge du mode arrière-plan a été introduite.
* **Zendesk # 17409 :**
Lorsque vous passez en mode de lecture de l’astuce, puis revenez en mode de lecture normal, puis revenez en mode de lecture de l’astuce, la position de lecture était le saut.
* **PTPLAY-9552 :**
Après l’analyse des fichiers XML de réponse, le code d’erreur 1108 est désormais ingéré chaque fois qu’il n’y a aucune publicité.
* **PTPLAY-9551 :**
En l’absence de coupure publicitaire après le traitement d’Auditude, CRS appelle 
**onPrefetchComplete** qui décrémente le groupCount. Comme il n’y a pas de coupure publicitaire, la variable **groupCount** est égal à 0 et décrémenté par 1. Auparavant, la variable **groupCount** was **uint32_t** car elle était utilisée pour passer à la valeur maximale. Ceci est maintenant **int32_t**.

**Version 2.1.0.621**

* **Zendesk #4555**
Problèmes instantanés sur la mémoire générant des erreurs de chargement - 
`MediaItemLoader` Correction d’un blocage survenant lors de la publication `mediaitemloader`

* **Zendesk #17223**
2.x CSAI : Toutes les URL de suivi des publicités ne se déclenchent pas
   * Certaines publicités VAST pointant à leur tour vers une publicité intégrée manquaient d’URL de suivi.
   * Lorsque plusieurs balises d’impression se trouvent dans une publicité au format XML VAST, seule la première URL d’impression a été enregistrée et le reste a été ignoré. Désormais, toutes les URL d’impression seront enregistrées et ingérées ultérieurement.
* **Zendesk #17224**
L’agent utilisateur PS4 déplace les informations d’heure d’avant vers la fin de la chaîne UAString
* **Zendesk #17226**
2.x CSAI : Toutes les publicités ne sont pas assemblées.
\
   Le correctif consiste à indiquer que la chronologie a changé en raison des opérations insertBy ou eraseBy et à faire basculer le point en conséquence.

* **Zendesk #17284**
   [Toutes les plateformes] Les sous-titres codés ne s’affichent pas.\
   HLS : prise en charge de la variable `EXT-X-MEDIA-TIME` balise pour les fichiers de sous-titres VTT.

* **Zendesk #17889**
Lecture &quot;Lactée&quot; sur PS4
\
   décalage correct appliqué (pour la conversion des couleurs)

* **Zendesk #17954**
Logique de secours de la publicité + gestion des espaces vides
\
   Correction du problème si l’un des wrappers Vast était vide, l’analyseur Vast était utilisé pour continuer le traitement de l’wrapper.

* **Zendesk #17807**
Impossible de passer devant un vaste vide Identique à Zendesk #3103

* **Zendesk #17865**
Logique de secours sur PS4 et XBox One
\
   Identique à Zendesk #3103

**Version 2.1.0.591**

* **Zendesk #3767**
Fragment de code de publicité PS4, la résolution de publicité échoue lors du traitement des redirections VMAP.
* **Zendesk #4096**
CSAI PS4 : Erreur de segmentation Correction d’un blocage lorsque TVSDK générait une erreur de segmentation lorsque la bibliothèque d’annonces traitait une réponse VMAP.

* **Zendesk #4161**
Le scénario 16x à la fin du film bloque l’impasse fixe qui se produit lorsque le scénario revient à la lecture normale.

* **Zendesk #4208**
Blocage aléatoire lorsque les sous-titres codés sont activés Fuite de mémoire fixe lorsque les sous-titres codés étaient activés

* **Zendesk #4213**
CSAI PS4 : Changer la chaîne par défaut de l’agent-utilisateur pour tous les appels liés à la publicité La chaîne de l’agent-utilisateur est créée à l’aide de la même chaîne UA que le navigateur utilise + ajouter une chaîne Primetime

* **PTPLAY-7675** (interne) Les publicités transcodées ne sont pas lues en cas d’échec de l’outil de remarketing créatif lorsqu’elles ont été appelées dans une réponse VMAP ou VAST. Le correctif consiste à simplement lire le fichier multimédia à partir de la publicité au lieu de lire à partir de la ressource en cas de grandes publicités.

* **PTPLAY-7895** (interne) Lorsque `allowMultipleAds=false`, aucune publicité n’est lue Bogue corrigé où `allowMultipleAds` n’était pas correctement suivi.

* **PTPLAY-7896** (interne) Les publicités s’exécutent dans un ordre non séquentiel sur PS4 Correction d’un problème en raison duquel les publicités n’étaient pas dans l’ordre dans lequel elles apparaissaient dans les réponses XML.

* PS4 TVSDK a été retesté dans une mini-application au lieu d’un jeu.

**Version 2.1.0.563**

* **Zendesk #3868**
TVSDK prend-il en charge le SDK Playstation 2.5 TVSDK est désormais créé avec le SDK Playstation 2.5.

* **Zendesk #4093**
paires clé-valeur targetingInfo dans la requête Pt Ads.
\
   Un caractère de nouvelle ligne séparant les paires clé/valeur a été ajouté.

## Fonctionnalités prises en charge {#supported-features}

Les fonctionnalités suivantes sont prises en charge dans TVSDK 2.1 pour PlayStation 4 :

**Version 2.1.0.621**

* Secours de la publicité, chaînement des publicités dans la logique de sélection des publicités (Zendesk #3103) Pour les publicités VAST (créatives) avec la règle de secours activée, le TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

**Version 2.1.0.538**

* Lecture VOD HLS incluant lecture, pause, recherche
* Diffusion en continu à débit adaptatif
* Lecture de contenu chiffré avec du contenu protégé par Primetime DRM et vanilla AES
* Insertion de publicités côté client avec comportements de publicité par défaut et annulation de publicités
* Reconditionnement créatif
* Sous-titres WebVTT fermés
* Installez-le avec la position de départ personnalisée
* Lecture rapide et rapide
* 302 redirect

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://experienceleague.adobe.com/docs/primetime.html) page.
