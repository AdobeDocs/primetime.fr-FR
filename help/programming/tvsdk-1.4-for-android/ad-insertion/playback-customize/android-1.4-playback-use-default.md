---
description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-title: Utiliser le comportement de lecture par défaut
title: Utiliser le comportement de lecture par défaut
uuid: ccda5223-17c1-4cda-b875-e706f5dc8648
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Utiliser le comportement de lecture par défaut {#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.

Pour utiliser les comportements par défaut :

    * Si vous implémentez votre propre classe &quot;AdvertisingFactory&quot;, renvoyez la valeur null pour &quot;createAdPolicySelector&quot;.
    
    * Si vous n’avez pas d’implémentation personnalisée pour la classe &quot;AdvertisingFactory&quot;, TVSDK utilise un sélecteur de stratégie d’annonce par défaut.