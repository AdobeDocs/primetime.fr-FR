---
title: Partie initiale du contenu dans le effacement
description: Partie initiale du contenu dans le effacement
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Partie initiale du contenu dans le effacement{#initial-portion-of-content-in-the-clear}

Ce paramètre facultatif spécifie une durée (en secondes) à partir du début du contenu qui ne sera pas chiffré.

Exemple de cas d’utilisation : cela permet un temps de démarrage de lecture plus rapide, tandis que le client Primetime DRM télécharge la licence en arrière-plan. La partie non chiffrée de la vidéo commence immédiatement la lecture alors que l’initialisation et l’acquisition de licences se produisent en arrière-plan. Lorsque cette fonction est désactivée, les utilisateurs peuvent constater un retard dans l’expérience de lecture, car l’ordinateur client effectue toutes les étapes de licence avant qu’une lecture vidéo ne puisse avoir lieu.
