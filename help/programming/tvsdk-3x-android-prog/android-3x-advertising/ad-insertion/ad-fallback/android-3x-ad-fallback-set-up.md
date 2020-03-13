---
description: Vous pouvez activer la reprise lorsqu’une publicité VMAP intégrée contient un type de média non valide.
seo-description: Vous pouvez activer la reprise lorsqu’une publicité VMAP intégrée contient un type de média non valide.
seo-title: Définir le comportement des publicités de secours pour les annonces VMAP intégrées
title: Définir le comportement des publicités de secours pour les annonces VMAP intégrées
uuid: bc8cb0b4-5ea9-429b-ab5d-746c6f03e74b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Définir le comportement des publicités de secours pour les annonces VMAP intégrées {#define-fallback-ad-behavior-for-vmap-inline-ads}

Vous pouvez activer la reprise lorsqu’une publicité VMAP intégrée contient un type de média non valide.

1. Définissez `setFallbackOnInvalidCreativeEnabled` `true` la valeur VMAP pour qu’elle soit renvoyée lorsque le type de média d’une publicité linéaire/intégrée n’est pas valide pour HLS.

   La valeur par défaut est `false`. Si une publicité linéaire échoue en raison d’un type de média non valide ou parce que la publicité ne peut pas être reconditionnée, cet indicateur permet à Primetime et à la décision de suivre le même comportement de secours que si la publicité était un wrapper VAST vide.

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```
