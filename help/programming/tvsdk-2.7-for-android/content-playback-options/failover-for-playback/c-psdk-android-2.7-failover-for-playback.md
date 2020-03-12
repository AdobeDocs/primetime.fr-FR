---
description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
seo-description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
seo-title: Lecture et basculement
title: Lecture et basculement
uuid: 7bbca3fe-88a3-4384-9a63-eb164c956a75
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#playback-and-failover-overview}

La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.

>[!IMPORTANT]
>
>Primetime ne peut pas se protéger des défaillances telles qu&#39;une panne de FAI ou une déconnexion de câble.

La diffusion en flux continu Primetime offre une protection contre le basculement afin de protéger la lecture de certaines défaillances du serveur distant ou de certaines défaillances opérationnelles, ce qui améliore la visualisation. Malgré les problèmes de transmission, TVSDK met en oeuvre une protection contre le basculement afin de minimiser les interruptions de lecture et d’obtenir une lecture fluide. Le lecteur vidéo bascule automatiquement vers une visionneuse de supports de sauvegarde lorsque des rendus ou des fragments entiers ne sont pas disponibles.