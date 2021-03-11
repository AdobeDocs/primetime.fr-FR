---
description: TVSDK contacte un service de diffusion publicitaire, tel que la prise de décision publicitaire Adobe Primetime, et tente d’obtenir le fichier de liste de lecture Principal qui correspond au flux vidéo de la publicité. Au cours de la phase de résolution des publicités, TVSDK effectue un appel HTTP au serveur de diffusion publicitaire distant et analyse la réponse du serveur.
title: Phase de résolution des publicités
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Phase de résolution des publicités{#ad-resolving-phase}

TVSDK contacte un service de diffusion publicitaire, tel que la prise de décision publicitaire Adobe Primetime, et tente d’obtenir le fichier de liste de lecture Principal qui correspond au flux vidéo de la publicité. Au cours de la phase de résolution des publicités, TVSDK effectue un appel HTTP au serveur de diffusion publicitaire distant et analyse la réponse du serveur.

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
