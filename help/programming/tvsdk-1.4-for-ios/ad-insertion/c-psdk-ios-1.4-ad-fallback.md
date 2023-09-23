---
description: Pour les publicités (ou créatives) du modèle de diffusion de publicités vidéo numérique (VAST) pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.
title: Reprise de publicité pour les publicités VAST et VMAP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Reprise de publicité pour les publicités VAST et VMAP {#ad-fallback-for-vast-and-vmap-ads}

Pour les publicités (ou créatives) du modèle de diffusion de publicités vidéo numérique (VAST) pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

La spécification VAST/Digital Video Multiple Ad Playlist (VMAP) indique que pour les publicités pour lesquelles le secours VAST est activé, les publicités vides déclenchent automatiquement l’utilisation des publicités de secours. Lorsqu’une publicité VAST est vide, TVSDK recherche un remplacement de type de média HLS valide parmi les publicités de secours. Lorsqu’une publicité VAST dans un wrapper possède un type de média non valide, TVSDK traite cette publicité comme vide. Vous pouvez configurer TVSDK pour qu’il fasse de même pour les publicités intégrées dans un VMAP. Pour plus d’informations sur VAST `fallbackOnNoAd` fonctionnalité, voir [Modèle de diffusion de publicités vidéo numériques (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

## Définition du comportement des publicités de secours pour les publicités intégrées VMAP {#section_D90BB3C6E539472EABF000C0F616DBE2}

Vous pouvez activer la version de secours lorsqu’une publicité VMAP intégrée contient un type de média non valide.

1. Définir `FallbackOnInvalidCreativeEnabled` to `YES` pour que VMAP soit rétroactif lorsque le type de média pour une publicité linéaire/intégrée n’est pas valide pour HLS.

   >[!NOTE]
   >
   >La valeur par défaut est NO. Si une publicité linéaire échoue parce qu’elle possède un type de média non valide ou parce que la publicité ne peut pas être reconditionnée, cet indicateur permet à Primetime et à la prise de décision publicitaire de suivre le même comportement de secours que si la publicité était un wrapper VAST vide.

   ```
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.isFallbackOnInvalidCreativeEnabled = YES;
   ```

## Comportement de secours des publicités pour VAST et VMAP {#section_5B6716CC49CC4C40964CFE9F122C57A6}

Lorsque la prise de décision relative aux publicités Primetime rencontre une publicité VAST (créative) vide ou ayant un type de média non valide pour HLS, elle évalue les publicités de secours pour déterminer ce qui doit être renvoyé.

Dans TVSDK, le seul type de média valide est `application/x-mpegURL` (M3U8).

Lorsqu’il existe des publicités de secours autonomes, le plug-in de prise de décision publicitaire Primetime examine ces publicités dans l’ordre suivant et renvoie la première publicité avec un type de média valide :

1. Si le reconditionnement est activé, la première occurrence d’une publicité avec un type de média non valide est traitée comme d’autres types de média non valides.

   Si le reconditionnement échoue, ce processus s’applique aux occurrences supplémentaires de la publicité.
1. Si TVSDK ne trouve aucune publicité de secours valide, il renvoie la publicité d’origine avec le type de média non valide.
1. Si une publicité de secours avec un type MIME valide est renvoyée au lieu de la publicité d’origine, Primetime et la prise de décision envoie le code d’erreur 403 à l’URL d’erreur VAST, le cas échéant.
1. Si une publicité de secours est un wrapper qui renvoie plusieurs publicités, seules les publicités avec le type de média approprié sont renvoyées.

>[!IMPORTANT]
>
>Ce comportement est toujours activé pour les publicités dans les wrappers VAST. Pour les publicités VAST intégrées dans un VMAP, le comportement est désactivé par défaut, mais votre application peut l’activer.
