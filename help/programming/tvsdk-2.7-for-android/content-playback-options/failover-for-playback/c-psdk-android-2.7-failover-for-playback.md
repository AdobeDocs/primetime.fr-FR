---
description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d'un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
title: Lecture et basculement
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Aperçu {#playback-and-failover-overview}

La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d&#39;un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.

>[!IMPORTANT]
>
>Primetime ne peut pas se protéger des défaillances telles qu&#39;une panne de fournisseur de services Internet ou une déconnexion de câble.

La diffusion en flux continu Primetime assure une protection contre le basculement afin de protéger la lecture de certaines défaillances du serveur distant ou de certains échecs opérationnels, ce qui améliore l’affichage. Malgré les problèmes de transmission, TVSDK met en oeuvre une protection contre le basculement afin de minimiser les interruptions de lecture et d’obtenir une lecture transparente. Le lecteur vidéo bascule automatiquement sur une visionneuse de supports de sauvegarde lorsque des rendus ou des fragments entiers ne sont pas disponibles.