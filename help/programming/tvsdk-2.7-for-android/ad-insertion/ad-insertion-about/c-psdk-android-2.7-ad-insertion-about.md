---
description: L’insertion d’une publicité résout les publicités pour la vidéo à la demande (VOD), pour la diffusion en continu en direct et pour la diffusion linéaire avec le suivi des publicités et la lecture des publicités. TVSDK envoie les requêtes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et les place par étapes dans le contenu.
title: Insérer des annonces
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# Aperçu {#insert-ads-overview}

L’insertion d’une publicité résout les publicités pour la vidéo à la demande (VOD), pour la diffusion en continu en direct et pour la diffusion linéaire avec le suivi des publicités et la lecture des publicités. TVSDK envoie les requêtes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et les place par étapes dans le contenu.

Un *`ad break`* contient une ou plusieurs publicités lues en séquence. TVSDK insère des publicités dans le contenu principal en tant que membres d’une ou de plusieurs coupures publicitaires.

>[!NOTE]
>
>Si la publicité comporte des erreurs, TVSDK ignore la publicité.