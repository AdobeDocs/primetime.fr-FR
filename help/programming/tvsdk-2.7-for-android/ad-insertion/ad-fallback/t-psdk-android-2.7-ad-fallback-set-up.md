---
description: Vous pouvez activer la solution de secours lorsqu’une publicité VMAP intégrée contient un type de média non valide.
title: Définition du comportement des publicités de secours pour les publicités intégrées VMAP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Définition du comportement des publicités de secours pour les publicités intégrées VMAP {#define-fallback-ad-behavior-for-vmap-inline-ads}

Vous pouvez activer la solution de secours lorsqu’une publicité VMAP intégrée contient un type de média non valide.

1. Définir `setFallbackOnInvalidCreativeEnabled` to `true` pour que VMAP soit rétroactif lorsque le type de média pour une publicité linéaire/intégrée n’est pas valide pour HLS.

   La valeur par défaut est `false`. Si une publicité linéaire échoue parce qu’elle possède un type de média non valide ou parce que la publicité ne peut pas être reconditionnée, cet indicateur permet à Primetime et à la prise de décision de prendre le même comportement de secours que si la publicité était un wrapper VAST vide.

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```
