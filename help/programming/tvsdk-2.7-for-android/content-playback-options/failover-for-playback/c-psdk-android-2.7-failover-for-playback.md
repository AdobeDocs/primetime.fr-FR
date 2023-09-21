---
description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
title: Lecture et basculement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Présentation {#playback-and-failover-overview}

La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.

>[!IMPORTANT]
>
>Primetime ne peut pas se protéger des défaillances telles qu&#39;une panne de FAI ou une déconnexion de câble.

La diffusion en continu Primetime fournit une protection de basculement pour protéger la lecture de certaines défaillances du serveur distant ou d’échecs opérationnels, ce qui améliore l’expérience de visionnage. Malgré les problèmes de transmission, TVSDK met en oeuvre une protection de basculement afin de minimiser les interruptions de lecture et d’obtenir une lecture transparente. Le lecteur vidéo bascule automatiquement vers une visionneuse de médias de sauvegarde lorsque des rendus ou des fragments entiers ne sont pas disponibles.
