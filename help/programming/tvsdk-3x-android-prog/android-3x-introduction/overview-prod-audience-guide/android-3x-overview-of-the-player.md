---
description: TVSDK pour Android 3.4 comprend diverses fonctionnalités que vous pouvez mettre en oeuvre dans vos lecteurs.
seo-description: TVSDK pour Android 3.4 comprend diverses fonctionnalités que vous pouvez mettre en oeuvre dans vos lecteurs.
seo-title: Fonctionnalités de TVSDK Primetime
title: Fonctionnalités de TVSDK Primetime
uuid: 6e26c09c-2858-47d1-80e8-1d7c6a468b86
translation-type: tm+mt
source-git-commit: ad58732842eb651514a47dd565e31e3d98a84c46
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Fonctionnalités de TVSDK Primetime {#primetime-tvsdk-features}

TVSDK pour Android 3.9 comprend diverses fonctionnalités que vous pouvez mettre en oeuvre dans vos lecteurs.

Fonctionnalités de TVSDK :

* **VOD et lecture en direct/linéaire**

   * Gestion de la fenêtre de lecture, y compris les méthodes permettant de lire, arrêter, suspendre, rechercher et récupérer la position du curseur de lecture
   * Prise en charge de la relecture en événement complet
   * Sous-titrage (608, 708, WebVTT) et autres formes audio pour une accessibilité accrue
   * Commandes de style de texte dans les légendes
   * Fonctionnalités DVR, avance rapide et retour rapide (ces deux dernières sont connues sous le nom de *mode de lecture de l’astuce*)
   * Logique de débit adaptatif (ABR) et configuration initiale des contrôles ABR
   * Prise en charge du basculement du manifeste en direct
   * Tampons de lecture réglables
   * Prise en charge du suivi de la durée, de la taille et du délai de téléchargement des fragments

* **Publicité**

   * VPAID 2.0
   * Collecte de publicités côté client

      * Insertion d’annonces en toute transparence, y compris la prise en charge de VAST/VMAP
      * Prise en charge des balises de repère personnalisées pour les publicités
      * Prise en charge du marquage, du remplacement et de la suppression des publicités C3
      * Flux de travaux personnalisable d&#39;insertion de contenu/publicités, y compris le signalement d&#39;interruption de service

* **Protection du contenu**

   * Accès aux services liés à la gestion des droits numériques
   * Lecture des flux HLS non chiffrés ou avec la diffusion en flux continu HTTP en direct protégée (PHLS)
   * Contrôle de la sortie basé sur la résolution, basé sur la stratégie DRM

* **Suivi des vidéos et des publicités**

   * Suivi des événements QoS
   * Notifications qui aident TVSDK et votre application à communiquer de manière asynchrone sur l’état des vidéos, publicités et autres éléments. Les notifications consignent également l’activité.

* **Journalisation**

   * Journalisation du débogage
   * Prise en charge du suivi de la durée, de la taille et du délai de téléchargement des fragments.

* **Diffusion sécurisée**

   * Prise en charge de la diffusion sécurisée (HTTPS) pour tous les appels provenant de TVSDK.