---
description: TVSDK contacte un service de diffusion publicitaire, tel que la prise de décision publicitaire Adobe Primetime, et tente d’obtenir le fichier de liste de lecture principal qui correspond au flux vidéo de la publicité. Pendant la phase de résolution de la publicité, TVSDK effectue un appel HTTP au serveur de diffusion de publicité distante et analyse la réponse du serveur.
title: Phase de résolution des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Phase de résolution des publicités{#ad-resolving-phase}

TVSDK contacte un service de diffusion publicitaire, tel que la prise de décision publicitaire Adobe Primetime, et tente d’obtenir le fichier de liste de lecture principal qui correspond au flux vidéo de la publicité. Pendant la phase de résolution de la publicité, TVSDK effectue un appel HTTP au serveur de diffusion de publicité distante et analyse la réponse du serveur.

TVSDK prend en charge les types de fournisseurs d’annonces suivants :

* Fournisseur de publicités de métadonnées

  Les données de publicité sont codées dans des fichiers JSON en texte brut.
* Fournisseur d’annonces de prise de décision publicitaire Primetime

  TVSDK envoie une demande, y compris un ensemble de paramètres de ciblage et un numéro d’identification de ressource, au serveur principal Primetime ad Decisioning. La prise de décision publicitaire Primetime répond avec un document SMIL (synchrone media integration language) qui contient les informations de publicité requises.
* Fournisseur de marketing publicitaire personnalisé

  Gère la situation où les publicités sont brûlées dans le flux, du côté serveur. TVSDK n’effectue pas l’insertion de publicités proprement dite, mais il doit effectuer le suivi des publicités insérées côté serveur. Ce fournisseur définit les marqueurs publicitaires utilisés par TVSDK pour effectuer le suivi des publicités.

L’une des situations de basculement suivantes peut se produire au cours de cette phase :

* Les données ne peuvent pas être récupérées pour des raisons telles qu’un manque de connectivité ou une erreur côté serveur, telle qu’une ressource introuvable, etc.
* Les données ont été récupérées, mais le format n’est pas valide.

  Cela peut se produire car, par exemple, l’analyse des données entrantes a échoué.

TVSDK émet une notification d’avertissement à propos de l’erreur et continue le traitement.
