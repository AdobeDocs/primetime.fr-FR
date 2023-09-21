---
description: L’insertion de publicités résout les publicités pour la diffusion vidéo à la demande (VOD), pour la diffusion en direct et pour la diffusion en continu linéaire avec suivi des publicités et lecture de publicité. TVSDK envoie les demandes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et place les publicités dans le contenu par phases.
title: Insérer des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Présentation {#insert-ads-overview}

L’insertion de publicités résout les publicités pour la diffusion vidéo à la demande (VOD), pour la diffusion en direct et pour la diffusion en continu linéaire avec suivi des publicités et lecture de publicité. TVSDK envoie les demandes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et place les publicités dans le contenu par phases.

Une coupure publicitaire contient une ou plusieurs publicités lues en séquence. TVSDK insère des publicités dans le contenu principal en tant que membres d’une ou de plusieurs coupures publicitaires.

>[!TIP]
>
>Si la publicité comporte des erreurs, TVSDK l’ignore.
