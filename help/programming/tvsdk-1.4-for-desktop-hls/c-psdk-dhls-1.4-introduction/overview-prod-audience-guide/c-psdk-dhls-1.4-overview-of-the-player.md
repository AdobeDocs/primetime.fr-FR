---
description: 'TVSDK pour Desktop HLS comprend diverses fonctionnalités et fournit les principales fonctionnalités suivantes : '
title: Fonctionnalités de Primetime TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Fonctionnalités de Primetime TVSDK{#primetime-tvsdk-features}

TVSDK pour Desktop HLS comprend diverses fonctionnalités et fournit les principales fonctionnalités suivantes :

* Lecture VOD et linéaire

   * Gestion de la fenêtre de lecture, y compris les méthodes permettant de lire, arrêter, mettre en pause, rechercher et récupérer la position du curseur de lecture.
   * Sous-titrage codé (608, 708, WebVTT) et autres formes audio pour une accessibilité accrue
   * Contrôle du style de texte dans les légendes
   * Fonctionnalité de l’enregistrement numérique (DVR), revirement rapide/rapide (mode de lecture de l’aperçu)
   * Lecture de la vidéo pour le contenu en direct et VOD
   * Logique de débit adaptatif (ABR) et configuration initiale des contrôles ABR
   * Prise en charge du basculement du manifeste en direct
   * Mémoires de lecture ajustables
   * Optimisation de la redirection 302
   * Prise en charge du suivi de la durée, de la taille et de la durée de téléchargement des fragments

* Publicité

   * VPAID 2.0
   * Groupement publicitaire côté client

      * Insertion de publicités transparente, notamment prise en charge de VAST/VMAP
      * Prise en charge des balises de repère personnalisées pour les publicités
      * Prise en charge du marquage, du remplacement et de la suppression des publicités C3
      * Processus personnalisable d’insertion de contenu/de publicités, y compris le signal d’arrêt

* Protection du contenu

   * Accès aux services liés à la gestion des droits numériques
   * Lecture des diffusions HLS non chiffrées ou avec la diffusion en continu HTTP protégée (PHLS)
   * Contrôle de sortie basé sur la résolution, basé sur la stratégie DRM
   * Prise en charge des cookies de session et de l’authentification multimédia
   * Combinaison de jetons de domaines multiples

* Suivi vidéo et publicitaire

   * Suivi des événements QoS
   * Notifications qui aident TVSDK et votre application à communiquer de manière asynchrone sur l’état des vidéos, publicités et autres éléments, ainsi que sur cette activité de journal.
   * Intégration à Adobe Analytics et prise en charge de pulsation

* Journalisation

   * Journalisation de débogage.
   * Prise en charge du suivi pour la durée, la taille et la durée de téléchargement des fragments.
