---
description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
title: Utiliser le comportement de lecture par défaut
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---


# Utiliser le comportement de lecture par défaut {#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.

Pour utiliser des comportements par défaut :

    * Si vous implémentez votre propre classe &quot;AdvertisingFactory&quot;, renvoyez la valeur null pour &quot;createAdPolicySelector&quot;.
    
    * Si vous n’avez pas d’implémentation personnalisée pour la classe &quot;AdvertisingFactory&quot;, TVSDK utilise un sélecteur de stratégie d’annonce par défaut.