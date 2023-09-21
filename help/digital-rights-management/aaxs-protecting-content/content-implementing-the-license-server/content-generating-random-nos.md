---
title: Générer des nombres aléatoires
description: Générer des nombres aléatoires
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Générer des nombres aléatoires{#generating-random-numbers}

Des générateurs de nombres aléatoires matériels peuvent être utilisés sur les serveurs Linux pour s’assurer qu’une entropie suffisante est générée. Si la machine ne parvient pas à générer suffisamment d’entropie, les opérations d’accès à l’Adobe nécessitant une source aléatoire se bloquent en attendant les données provenant de `/dev/random`.
