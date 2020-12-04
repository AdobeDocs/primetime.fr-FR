---
title: Notes de mise à jour de TVSDK 2.1 PlayStation 4
seo-title: Notes de mise à jour de TVSDK 2.1 PlayStation 4
description: Les notes de mise à jour de TVSDK 2.1 pour PlayStation 4 décrivent les fonctionnalités prises en charge et les problèmes connus de TVSDK 2.1 PlayStation 4.
seo-description: Les notes de mise à jour de TVSDK 2.1 pour PlayStation 4 décrivent les fonctionnalités prises en charge et les problèmes connus de TVSDK 2.1 PlayStation 4.
uuid: 494569cf-07e2-476a-b88e-e46c9cca4cdc
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: ebfc8819-f5a9-47a2-b454-0e4e6f9e4640
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# Notes de mise à jour de TVSDK 2.1 PlayStation 4 {#tvsdk-playstation-release-notes}

Les notes de mise à jour de TVSDK 2.1 pour PlayStation 4 décrivent les fonctionnalités prises en charge et les problèmes connus de TVSDK 2.1 PlayStation 4.

## Problèmes résolus {#resolved-issues}

Voici les problèmes résolus pour TVSDK 2.1 pour PlayStation 4 :

**Version 2.1.0.638**

* **PTPLAY-10439 :**
Lorsque le lien publicitaire d’enveloppe VMAP a été rompu, le lecteur se retrouvait bloqué dans l’état Préparation (il n’envoyait pas de message) 
`onComplete` à son appelant).

* **PTPLAY-10179 :**

   `creativeRepackaging` et  `fallbackOnInvalidCreative` les valeurs sont désormais désactivées par défaut. En outre, lorsque l&#39;indicateur `creativeRepackaging` a été défini mais qu&#39;aucun format `creativeRepackaging` n&#39;a été fourni, `onRepackagingComplete` était appelé autant de fois qu&#39;il y avait des publicités dans la coupure publicitaire, ce qui entraînait la création de pauses publicitaires à plusieurs reprises.

* **Zendesk #10304** : La variable d’annulation d’annonce activée/désactivée n’a pas été initialisée. Nous initialisons désormais la variable à partir du ctor `DataSetEntry's`.

* **PTPLAY-10318 :**
Prise en charge du mode arrière-plan.
* **Zendesk # 17409:**
Lorsque vous passez en mode de lecture par astuces, puis revenez en mode de lecture normal, puis de nouveau en mode de lecture par astuces, la position de lecture était en train de sauter.
* **PTPLAY-9552 :**
Après avoir analysé les fichiers XML de réponse, le code d’erreur 1108 est maintenant épinglé chaque fois qu’il n’y a aucune publicité.
* **PTPLAY-9551:**
Lorsqu&#39;il n&#39;y a pas de coupure publicitaire après le traitement d&#39;Auditude, le CRS appelle 
**** onPrefetchCompletequi décrémente le groupCount. Comme il n’y a pas de coupure publicitaire, **groupCount** est égal à 0 et décrété par 1. Auparavant, **groupCount** était **uint32_t** en raison duquel il était utilisé pour passer à la valeur maximale. Il s’agit maintenant de **int32_t**.

**Version 2.1.0.621**

* **Zendesk #4555**
Instant sur les problèmes de mémoire générant des erreurs de chargement - 
`MediaItemLoader` Correction d’un blocage survenant lors de la libération  `mediaitemloader`

* **Zendesk #17223**
2.x CSAI : Toutes les URL de suivi des publicités ne se déclenchent pas
   * Certaines publicités VAST pointant à leur tour vers une publicité intégrée manquaient d’URL de suivi.
   * Lorsqu’une publicité contenait plusieurs balises d’impression dans le format XML VAST, seule la première url d’impression était enregistrée et le reste était ignoré. Désormais, toutes les url d’impression seront enregistrées et épinglées ultérieurement.
* **Zendesk #17224**
PS4 L’agent utilisateur déplace les informations d’heure de début à la fin de la chaîne UAString
* **Zendesk #17226**
2.x CSAI : Toutes les publicités ne sont pas assemblées.
\
   Le correctif consiste à indiquer que la chronologie a changé en raison des opérations insertBy ou eraseBy et à faire basculer la période en conséquence.

* **Zendesk #17284**
   [Toutes les ] plateformesLes légendes fermées ne s’affichent pas.\
   HLS : prise en charge de la balise `EXT-X-MEDIA-TIME` pour les fichiers de sous-titrage VTT.

* **Zendesk #17889**
Lecture &quot;Lactée&quot; sur PS4
\
   décalage correct appliqué (pour la conversion des couleurs)

* **Zendesk n° 17954**
Logique de secours publicitaire + gestion des annonces vides
\
   Correction d’un problème en raison duquel l’un des wrappers Vast était vide, l’analyseur Vast continuait à traiter le wrapper.

* **Zendesk #17807**
Impossible de dépasser vide vaste Identique à Zendesk #3103

* **Zendesk #17865**
Fallback Logic sur PS4 et XBox One
\
   Identique à Zendesk #3103

**Version 2.1.0.591**

* **Le fragment de code de publicité Zendesk #3767**
PS4 échoue lors du traitement des redirections VMAP.
* **Zendesk #4096**
PS4 CSAI : Défaillance de segmentation Correction d’un blocage lorsque TVSDK lançait une erreur de segmentation lorsque la bibliothèque publicitaire traitait une réponse VMAP.

* **Zendesk #4161**
Trickplay 16x à la fin du film gèle l&#39;impasse fixe survenant lorsque le trickplay revient à la lecture normale

* **Zendesk #4208**
Blocage aléatoire lorsque les sous-titres fermés sont activés Correction d’une fuite de mémoire lorsque les sous-titres fermés étaient activés

* **Zendesk #4213**
PS4 CSAI : Changer la chaîne par défaut user-agent pour tous les appels liés à la publicité La chaîne User-agent est créée à l’aide de la même chaîne UA que celle utilisée par le navigateur + ajouter une chaîne Primetime

* **PTPLAY-7675**  (interne) Les publicités transcodées ne lisant pas Creative Repackaging échouaient lorsqu’elles appelaient dans une réponse VMAP ou VAST. Le correctif consiste à simplement lire le fichier média à partir de la publicité au lieu de lire à partir de la ressource en cas de grandes publicités.

* **PTPLAY-7895** (interne) Lorsque  `allowMultipleAds=false`aucune publicité n&#39;est lue Correction d&#39;un bogue quand  `allowMultipleAds` le paramètre n&#39;était pas correctement suivi.

* **PTPLAY-7896**  (interne) Les publicités s’exécutent en séquence sur PS4 Correction d’un problème en raison duquel les publicités n’étaient pas dans l’ordre dans lequel elles apparaissaient dans les réponses XML.

* PS4 TVSDK a été testé dans une mini-application plutôt que dans un jeu.

**Version 2.1.0.563**

* **Zendesk #3868**
TVSDK prend-il en charge le SDK Playstation 2.5 Le SDK TVSDK est maintenant créé avec le SDK Playstation 2.5.

* **Zendesk #4093**
targetingInfo paires clé-valeur dans la demande Publicités Pt.
\
   Un caractère de nouvelle ligne séparant les paires clé/valeur a été ajouté.

## Fonctionnalités prises en charge {#supported-features}

Les fonctionnalités suivantes sont prises en charge dans TVSDK 2.1 pour PlayStation 4 :

**Version 2.1.0.621**

* Abandon de publicité, chaînement de la marguerite dans la logique de sélection des publicités (Zendesk #3103)
Pour les publicités VAST (créatives) pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d&#39;utiliser des publicités de secours à sa place.Vous pouvez configurer certains aspects du comportement de secours

**Version 2.1.0.538**

* Lecture VOD HLS, y compris lecture, pause, recherche
* Diffusion en flux continu adaptative à débit binaire
* Lecture de contenu chiffré avec le contenu protégé par DRM Primetime et le contenu protégé par AES vanille
* Insertion publicitaire côté client avec comportements publicitaires par défaut et annulation de publicité
* Reconditionnement créatif
* Sous-titres WebVTT fermés
* Instantané avec position de début personnalisée
* Jouer à la vitesse supérieure et rembobiner rapidement
* 302 redirection

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à la [page Apprentissage et support Adobe Primetime](https://helpx.adobe.com/support/primetime.html).