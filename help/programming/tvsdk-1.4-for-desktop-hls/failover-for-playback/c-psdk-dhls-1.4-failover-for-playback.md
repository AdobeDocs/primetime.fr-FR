---
description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
title: Lecture et basculement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Présentation {#playback-and-failover-overview}

La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.

Primetime ne peut pas se protéger de telles pannes qu&#39;une panne de FAI ou une déconnexion de câble. Toutefois, la diffusion en continu Primetime fournit une protection de basculement pour protéger la lecture de certains échecs de serveur distant ou opérationnels, ce qui améliore l’expérience des visionneuses. TVSDK met en oeuvre une protection contre le basculement afin de minimiser les interruptions de lecture et d’obtenir une lecture transparente en dépit des problèmes de transmission. Le lecteur vidéo bascule automatiquement vers une visionneuse de médias de sauvegarde lorsque des rendus ou des fragments entiers ne sont pas disponibles.
