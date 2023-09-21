---
description: Vous pouvez choisir d’utiliser les comportements de publicité par défaut.
title: Utilisation du comportement de lecture par défaut
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# Utilisation du comportement de lecture par défaut {#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements de publicité par défaut.

Pour utiliser les comportements par défaut :

    * Si vous implémentez votre propre classe `AdvertisingFactory`, renvoyez null pour `createAdPolicySelector` .
    
    * Si vous ne disposez pas d’une implémentation personnalisée pour la classe &quot;AdvertisingFactory&quot;, TVSDK utilise un sélecteur de stratégie de publicité par défaut.
