---
description: Dans certains cas, vous devez savoir si le contenu multimédia est actif ou VOD.
seo-description: Dans certains cas, vous devez savoir si le contenu multimédia est actif ou VOD.
seo-title: Déterminer si le contenu est actif ou VOD
title: Déterminer si le contenu est actif ou VOD
uuid: 4d514c46-a1d0-4721-a423-92108126e37e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Déterminer si le contenu est actif ou VOD{#identify-whether-the-content-is-live-or-vod}

Dans certains cas, vous devez savoir si le contenu multimédia est actif ou VOD.

1. Assurez-vous que le lecteur est au moins en état INITIALISÉ.
1. Déterminez si le `MediaPlayerItem` contenu est actif (true) ou VOD (false).

   ```
   function get isLive():Boolean;
   ```

