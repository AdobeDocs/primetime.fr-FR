---
description: Vous pouvez activer la reprise lorsqu’une publicité VMAP intégrée contient un type de média non valide.
seo-description: Vous pouvez activer la reprise lorsqu’une publicité VMAP intégrée contient un type de média non valide.
seo-title: Définir le comportement des annonces de secours pour les annonces VMAP intégrées
title: Définir le comportement des annonces de secours pour les annonces VMAP intégrées
uuid: a7b5c9a6-f546-4d3a-9d49-7e5484acff7a
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Définir le comportement des publicités de secours pour les annonces VMAP intégrées {#define-fallback-ad-behavior-for-vmap-inline-ads}

Vous pouvez activer la reprise lorsqu’une publicité VMAP intégrée contient un type de média non valide.

1. Définissez `setFallbackOnInvalidCreativeEnabled` sur `true` pour que VMAP soit rétabli lorsque le type de média pour une publicité linéaire/intégrée n&#39;est pas valide pour HLS.

   La valeur par défaut est `false`. Si une publicité linéaire échoue parce qu’elle est d’un type de média non valide ou parce que la publicité ne peut pas être reconditionnée, cet indicateur permet à Primetime et à la prise de décision de suivre le même comportement de secours que si la publicité était un wrapper VAST vide.

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```

