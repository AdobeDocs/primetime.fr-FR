---
description: Dans le cas des annonces (ou créatives) à modèle de diffusion de vidéo numérique pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.
seo-description: Dans le cas des annonces (ou créatives) à modèle de diffusion de vidéo numérique pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.
seo-title: Reprise publicitaire pour les annonces VAST et VMAP
title: Reprise publicitaire pour les annonces VAST et VMAP
uuid: 290f0aeb-7314-4615-b477-24e65d5857ac
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Reprise publicitaire pour les annonces VAST et VMAP {#ad-fallback-for-vast-and-vmap-ads}

Dans le cas des annonces (ou créatives) à modèle de diffusion de vidéo numérique pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

La spécification VAST/Digital Video Multiple Ad Playlist (VMAP) indique que pour les publicités pour lesquelles la reprise VAST est activée, les publicités vides déclenchent automatiquement l’utilisation des publicités de secours. Lorsqu’une publicité VAST est vide, TVSDK recherche un remplacement de type de média HLS valide parmi les annonces de secours. Lorsqu’une publicité VAST dans un wrapper a un type de média non valide, TVSDK traite cette publicité comme vide. Vous pouvez déterminer si TVSDK doit faire de même pour les publicités intégrées dans un VMAP. Pour plus d’informations sur la `fallbackOnNoAd` fonction VAST, voir Modèle de diffusion de publicités vidéo [numériques (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

## Définir le comportement des annonces de secours pour les annonces VMAP intégrées {#section_D90BB3C6E539472EABF000C0F616DBE2}

Vous pouvez activer la reprise lorsqu’une publicité VMAP intégrée contient un type de média non valide.

1. Définissez cette variable sur `FallbackOnInvalidCreativeEnabled` `YES` une réduction VMAP lorsque le type de média pour une publicité linéaire/intégrée n&#39;est pas valide pour HLS.

   >[!NOTE]
   >
   >La valeur par défaut est NO. Si une publicité linéaire échoue parce qu’elle est d’un type de média non valide ou parce que la publicité ne peut pas être reconditionnée, cet indicateur permet à la prise de décision publicitaire Primetime de suivre le même comportement de secours que si la publicité était un wrapper VAST vide.

   ```
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.isFallbackOnInvalidCreativeEnabled = YES;
   ```

## Comportement des abandons publicitaires pour VAST et VMAP {#section_5B6716CC49CC4C40964CFE9F122C57A6}

Lorsque la prise de décision publicitaire Primetime rencontre une publicité VAST (créative) vide ou dont le type de média n’est pas valide pour HLS, elle évalue les publicités de secours afin de déterminer ce qu’il faut renvoyer.

Dans TVSDK, le seul type de support valide est `application/x-mpegURL` (M3U8).

Lorsqu’il existe des publicités de secours autonomes, le module de prise de décision publicitaire Primetime examine ces publicités dans l’ordre suivant et renvoie la première avec un type de média valide :

1. Si le reconditionnement est activé, la première occurrence d’une publicité avec un type de média non valide est traitée comme d’autres types de média non valides.

   Si le reconditionnement échoue, ce processus s’applique aux occurrences supplémentaires de l’annonce.
1. Si TVSDK ne trouve aucune publicité de secours valide, il renvoie la publicité d’origine avec le type de média non valide.
1. Si une publicité de secours avec un type MIME valide est renvoyée au lieu de la publicité d’origine, la prise de décision publicitaire Primetime envoie le code d’erreur 403 à l’URL d’erreur VAST, si disponible.
1. Si une publicité de secours est un wrapper et renvoie plusieurs publicités, seules les publicités avec le type de média approprié sont renvoyées.

>[!IMPORTANT]
>
>Ce comportement est toujours activé pour les publicités dans les wrappers VAST. Pour les publicités VAST intégrées dans un VMAP, le comportement est désactivé par défaut, mais votre application peut l’activer.

