---
description: Pour les annonces (ou créatives) avec modèle de diffusion de publicité vidéo numérique (VAST) pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.
seo-description: Pour les annonces (ou créatives) avec modèle de diffusion de publicité vidéo numérique (VAST) pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.
seo-title: Abandon publicitaire pour les annonces VAST et VMAP
title: Abandon publicitaire pour les annonces VAST et VMAP
uuid: 290f0aeb-7314-4615-b477-24e65d5857ac
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Abandon publicitaire pour les annonces VAST et VMAP {#ad-fallback-for-vast-and-vmap-ads}

Pour les annonces (ou créatives) avec modèle de diffusion de publicité vidéo numérique (VAST) pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

La spécification VAST/Digital Video Multiple Ad Playlist (VMAP) indique que pour les publicités pour lesquelles la fonction de secours VAST est activée, les publicités vides déclenchent automatiquement l’utilisation des publicités de secours. Lorsqu’une publicité VAST est vide, TVSDK recherche un remplacement de type de média HLS valide parmi les annonces de secours. Lorsqu’une publicité VAST dans un wrapper a un type de média non valide, TVSDK traite cette publicité comme vide. Vous pouvez configurer si TVSDK doit faire de même pour les publicités intégrées dans un VMAP. Pour plus d’informations sur la `fallbackOnNoAd` fonctionnalité VAST, voir Modèle de diffusion de publicités vidéo [numérique (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

## Définir le comportement des publicités de secours pour les annonces VMAP intégrées {#section_D90BB3C6E539472EABF000C0F616DBE2}

Vous pouvez activer la reprise lorsqu’une publicité VMAP intégrée contient un type de média non valide.

1. Définissez `FallbackOnInvalidCreativeEnabled` `YES` la valeur VMAP pour qu’elle soit renvoyée lorsque le type de média d’une publicité linéaire/intégrée n’est pas valide pour HLS.

   >[!NOTE]
   >
   >La valeur par défaut est NO. Si une publicité linéaire échoue en raison d’un type de média non valide ou parce que la publicité ne peut pas être reconditionnée, cet indicateur permet à la prise de décision publicitaire Primetime de suivre le même comportement de secours que si la publicité était un wrapper VAST vide.

   ```
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.isFallbackOnInvalidCreativeEnabled = YES;
   ```

## Comportement de secours de publicité pour VAST et VMAP {#section_5B6716CC49CC4C40964CFE9F122C57A6}

Lorsque la prise de décision publicitaire Primetime rencontre une publicité VAST (créative) vide ou dont le type de média n’est pas valide pour HLS, elle évalue les publicités de secours afin de déterminer les éléments à renvoyer.

Dans TVSDK, le seul type de support valide est `application/x-mpegURL` (M3U8).

Lorsqu’il existe des publicités de secours autonomes, le module de prise de décision publicitaire Primetime examine ces publicités dans l’ordre suivant et renvoie la première publicité avec un type de média valide :

1. Si le reconditionnement est activé, la première occurrence d’une publicité avec un type de média non valide est traitée comme d’autres types de média non valides.

   Si le reconditionnement échoue, ce processus s’applique aux occurrences supplémentaires de la publicité.
1. Si TVSDK ne trouve aucune publicité de secours valide, il renvoie la publicité d’origine avec le type de média non valide.
1. Si une publicité de secours avec un type MIME valide est renvoyée au lieu de la publicité d’origine, la prise de décision publicitaire Primetime envoie le code d’erreur 403 à l’URL d’erreur VAST, le cas échéant.
1. Si une publicité de secours est un wrapper et renvoie plusieurs publicités, seules les publicités avec le type de média approprié sont renvoyées.

>[!IMPORTANT]
>
>Ce comportement est toujours activé pour les annonces dans les wrappers VAST. Pour les publicités VAST intégrées dans un VMAP, le comportement est désactivé par défaut, mais votre application peut l’activer.

