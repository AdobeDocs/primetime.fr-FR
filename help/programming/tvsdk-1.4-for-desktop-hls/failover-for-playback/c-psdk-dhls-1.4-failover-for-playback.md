---
description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d'un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité de lecture du média en local.
seo-description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d'un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité de lecture du média en local.
seo-title: Lecture et basculement
title: Lecture et basculement
uuid: 731c087d-9e14-4c7a-a856-c3962b9d7608
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Aperçu {#playback-and-failover-overview}

La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d&#39;un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité de lecture du média en local.

Primetime ne peut pas se protéger contre des pannes telles qu&#39;une panne de FAI ou une déconnexion de câble. Cependant, la diffusion en flux continu Primetime assure une protection contre le basculement afin de protéger la lecture de certaines défaillances du serveur distant ou de certaines défaillances opérationnelles, ce qui améliore l’expérience des visionneuses. TVSDK met en oeuvre une protection contre le basculement afin de minimiser les interruptions de lecture et d’obtenir une lecture transparente malgré les problèmes de transmission. Le lecteur vidéo bascule automatiquement sur une visionneuse de supports de sauvegarde lorsque des rendus ou des fragments entiers ne sont pas disponibles.
