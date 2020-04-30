---
description: Dans le cas des annonces (ou créatives) à modèle de diffusion de vidéo numérique pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.
keywords: zero length ad;empty ad
seo-description: Dans le cas des annonces (ou créatives) à modèle de diffusion de vidéo numérique pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.
seo-title: Reprise publicitaire pour les annonces VAST et VMAP
title: Reprise publicitaire pour les annonces VAST et VMAP
uuid: ecfeff31-b723-4a0d-99f2-48705a37b5f0
translation-type: tm+mt
source-git-commit: ''

---


# Présentation {#ad-fallback-for-vast-and-vmap-ads-overview}

Dans le cas des annonces (ou créatives) à modèle de diffusion de vidéo numérique pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

La spécification VAST/Digital Video Multiple Ad Playlist (VMAP) indique que pour les publicités pour lesquelles la fonction de secours VAST est activée, les publicités vides déclenchent automatiquement l’utilisation de publicités de secours. Lorsqu’une publicité VAST est vide, TVSDK recherche un remplacement de type de média HLS valide parmi les annonces de secours. Lorsqu’une publicité VAST dans un wrapper a un type de média non valide, TVSDK traite cette publicité comme vide. Vous pouvez déterminer si TVSDK doit faire de même pour les publicités intégrées dans un VMAP. Pour plus d’informations sur la `fallbackOnNoAd` fonction VAST, voir Modèle de diffusion de publicités vidéo [numériques (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

>[!NOTE]
>
>**Publicités** de longueur zéro - Lorsque TVSDK rencontre une réponse VAST contenant une publicité de durée nulle ou une coupure publicitaire sans publicité, elle déclenche des événements AD_BREAK_DÉBUT / AD_BREAK_COMPLETE pour ces coupures publicitaires de longueur nulle. *Ce comportement s’applique uniquement aux flux VOD.* TVSDK déclenche ces événements même si votre application utilise la stratégie d’annonce SKIP.
>
>TVSDK *ne déclenche pas* les événements AD_BREAK_DÉBUT / AD_BREAK_COMPLETE pour les flux en direct, ou lorsqu’un utilisateur utilise le trickplay ou cherche à dépasser la publicité de longueur nulle.

