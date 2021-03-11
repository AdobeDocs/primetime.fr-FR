---
title: Génération de nombres aléatoires
description: Génération de nombres aléatoires
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---


# Génération de nombres aléatoires{#generating-random-numbers}

Des générateurs de nombres aléatoires matériels peuvent être utilisés sur les serveurs Linux pour s&#39;assurer que l&#39;entropie est suffisante. Si l&#39;ordinateur ne parvient pas à générer suffisamment d&#39;entropie, les opérations d&#39;accès à l&#39;Adobe qui nécessitent une source de hasard se bloquent en attendant les données de `/dev/random`.
