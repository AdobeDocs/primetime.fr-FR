---
description: TVSDK contacte un service de diffusion publicitaire, tel qu’Adobe Primetime, et tente d’obtenir le fichier de liste de lecture principal correspondant au flux vidéo de la publicité. Au cours de la phase de résolution des publicités, TVSDK effectue un appel HTTP au serveur de diffusion publicitaire distant et analyse la réponse du serveur.
seo-description: TVSDK contacte un service de diffusion publicitaire, tel qu’Adobe Primetime, et tente d’obtenir le fichier de liste de lecture principal correspondant au flux vidéo de la publicité. Au cours de la phase de résolution des publicités, TVSDK effectue un appel HTTP au serveur de diffusion publicitaire distant et analyse la réponse du serveur.
seo-title: Phase de résolution des publicités
title: Phase de résolution des publicités
uuid: b3e62a57-7e62-4e4e-8fa6-0d416785db67
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Phase de résolution des publicités{#ad-resolving-phase}

TVSDK contacte un service de diffusion publicitaire, tel qu’Adobe Primetime, et tente d’obtenir le fichier de liste de lecture principal correspondant au flux vidéo de la publicité. Au cours de la phase de résolution des publicités, TVSDK effectue un appel HTTP au serveur de diffusion publicitaire distant et analyse la réponse du serveur.

TVSDK prend en charge les types de fournisseurs d’annonces suivants :

* Fournisseur d’annonces de métadonnées

   Les données publicitaires sont codées dans des fichiers JSON en texte brut.
* Fournisseur publicitaire de décision publicitaire Primetime

   TVSDK envoie une requête, y compris un ensemble de paramètres de ciblage et un numéro d’identification de ressource, au serveur principal Primetime et de prise de décision. La prise de décision publicitaire Primetime répond par un document SMIL (synchronized multimédia integration language) qui contient les informations publicitaires requises.
* Fournisseur de marques publicitaires personnalisées

   Gère la situation où les publicités sont brûlées dans le flux, du côté serveur. TVSDK n’effectue pas l’insertion réelle de la publicité, mais il doit effectuer le suivi des publicités insérées côté serveur. Ce fournisseur définit les marqueurs publicitaires utilisés par TVSDK pour effectuer le suivi des publicités.

Une des situations de basculement suivantes peut se produire pendant cette phase :

* Les données ne peuvent pas être récupérées pour des raisons telles qu&#39;un manque de connectivité ou une erreur côté serveur, telle qu&#39;une ressource introuvable, etc.
* Les données ont été récupérées, mais le format n&#39;est pas valide.

   Cela peut se produire en raison, par exemple, de l’échec de l’analyse des données entrantes.

TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.
