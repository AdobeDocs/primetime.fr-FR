---
description: Pour les publicités (ou créatives) du modèle de diffusion de publicités vidéo numérique (VAST) pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.
keywords: publicité de longueur nulle ; publicité vide
title: Reprise de publicité pour les publicités VAST et VMAP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Présentation {#ad-fallback-for-vast-and-vmap-ads-overview}

Pour les publicités (ou créatives) du modèle de diffusion de publicités vidéo numérique (VAST) pour lesquelles la règle de secours est activée, TVSDK traite une publicité avec un type de média non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

La spécification VAST/Digital Video Multiple Ad Playlist (VMAP) indique que pour les publicités pour lesquelles la fonction de secours VAST est activée, les publicités vides déclenchent automatiquement l’utilisation des publicités de secours. Lorsqu’une publicité VAST est vide, TVSDK recherche un remplacement de type de média HLS valide parmi les publicités de secours. Lorsqu’une publicité VAST dans un wrapper possède un type de média non valide, TVSDK traite cette publicité comme vide. Vous pouvez configurer TVSDK pour qu’il fasse de même pour les publicités intégrées dans un VMAP. Pour plus d’informations sur VAST `fallbackOnNoAd` fonctionnalité, voir [Modèle de diffusion de publicités vidéo numériques (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

>[!NOTE]
>
>**Zéro Longueur d’annonces** - Lorsque TVSDK rencontre une réponse VAST contenant une publicité de durée nulle, ou une coupure publicitaire sans publicité, il déclenche des événements AD_BREAK_START / AD_BREAK_COMPLETE pour ces coupures publicitaires de longueur nulle. *Ce comportement s’applique uniquement aux flux VOD.* TVSDK déclenche ces événements même si votre application utilise la stratégie de publicité SKIP.
>
>TVSDK fait *not* déclencher les événements AD_BREAK_START / AD_BREAK_COMPLETE pour les flux en direct, ou lorsqu’un utilisateur utilise le flux ou cherche à dépasser la publicité de longueur nulle.
